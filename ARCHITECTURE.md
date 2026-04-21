---
title: "NTNX Solutions Site Architecture"
lastupdate: git
lastupdateauthor: "Lakshmi Balaramane"
---

Focus on the **content flow**—specifically how source files from various repositories transform into a single customer-facing site.

Here is a template designed for a **Hub-and-Spoke** architecture using the Monorepo/Submodule approach.

---

# Architecture: Distributed Documentation Hub

## 1. Overview
This site follows a "Hub-and-Spoke" model. Subject Matter Experts (SMEs) maintain content in independent repositories, while this **Central Hub** aggregates that content into a unified, versioned customer-facing portal.



## 2. Component Structure
* **The Hub (This Repo):** Contains the global `mkdocs.yml`, theme customizations, and site-wide landing pages.
* **The Spokes (SME Repos):** Independent repositories containing domain-specific `.md` files and assets.
* **Build System:** Uses `mkdocs-material` with the `monorepo` plugin to merge navigation and search indexes.

## 3. Data Flow
Content is pulled and transformed through the following pipeline:

1.  **Ingestion:** CI/CD pipeline clones SME repositories into the `docs/` subdirectory via Git Submodules or `sparse-checkout`.
2.  **Aggregation:** The `mkdocs-monorepo-plugin` parses the `mkdocs.yml` files in each sub-directory.
3.  **Synthesis:** MkDocs-Material compiles the Markdown into a static HTML site with a unified global search index.
4.  **Versioning:** `mike` manages the deployment to specific versioned paths (e.g., `/v1.2/`, `/latest/`).



## 4. Ownership & Maintenance
| Component | Responsibility | Managed By |
| :--- | :--- | :--- |
| **Site UI/UX** | Global Theme & Plugins           | Platform Team |
| **Solution A** | Technical content for Solution A | SME Team A |
| **Solution B** | Technical content for Solution B | SME Team B |

## 5. Local Development
To run the full site locally:

```bash
# Clone with submodules
git clone --recursive <hub-repo-url>
pip install -r requirements.txt
mkdocs serve
```
---

### Key Logic for this Design:
* **Visualizes the Flow:** It treats the "Spokes" as data sources, making it clear that SMEs don't need to worry about the website's CSS or layout.
* **Separates Concerns:** Clearly defines who is responsible for the *content* versus who is responsible for the *infrastructure*.
* **Developer Friendly:** Includes the critical "How to run this" instruction, which is often missing from high-level architecture docs.

Would you like me to tailor the **Data Flow** section specifically to a CI/CD tool like GitHub Actions or GitLab CI?