---
title: "Continuous Integration Workflow"
lastupdate: git
lastupdateauthor: "Lakshmi Balaramane"
---

Integrating GitHub Actions into this architecture formalizes the "Source of Truth" vs. "Production View" relationship. In this setup, the Hub repository acts as the orchestrator.

Here is the updated **Data Flow** section tailored for a GitHub Actions workflow.

---

## 1. Data Flow (CI/CD via GitHub Actions)

The site utilizes GitHub Actions to automate the aggregation of distributed content. The workflow is triggered by pushes to the `main` branch of the Hub repo or on a scheduled basis to pull SME updates.

### Workflow Pipeline
1.  **Environment Setup:** The runner initializes Python and installs dependencies (MkDocs-Material, Monorepo plugin, Mike).
2.  **Content Ingestion:**
    * **Checkout:** The action checks out the Hub repository.
    * **Submodule Update:** `git submodule update --init --recursive --remote` is executed to pull the latest commits from all SME repositories.
3.  **Build & Validation:**
    * The `mkdocs-monorepo-plugin` validates that all SME sub-directories contain valid Markdown and internal references.
    * `mkdocs build` generates the unified static site.
4.  **Versioned Deployment:**
    * **mike deploy:** The built site is pushed to the `gh-pages` branch.
    * **Alias Management:** `mike` updates the `/latest/` or `/dev/` aliases to point to the new build.



### 2. Technical Implementation (GitHub Action Snippet)

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
          submodules: true # Ensures SME content is pulled

      - name: Update Submodules to Latest
        run: git submodule update --remote --recursive

      - name: Deploy with Mike
        run: |
          mike deploy --push --update-aliases 1.0 latest
```

---

### Why this works:

* **Decoupled Workflows:** SMEs can push to their own repos without breaking the main site. The main site only updates when the "Hub" CI runs.
* **Atomic Deployments:** By using `mike`, you ensure that the customer-facing site is updated in a single atomic operation, preventing "404 Not Found" errors during the build process.
* **Automated Sync:** Adding a `repository_dispatch` trigger or a `schedule` (cron) to the Hub's Action ensures that SME updates go live even if the Hub repository hasn't changed.

Does this alignment with GitHub Actions cover the automation level you were looking for?