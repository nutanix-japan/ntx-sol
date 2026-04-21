---
title: "Contributing Guide"
lastupdate: git
lastupdateauthor: "Lakshmi Balaramane"
---

The site uses a distributed architecture, the `CONTRIBUTING.md` needs to clearly distinguish between **Global (Hub)** contributions and **Domain (SME)** contributions.

Here are the essential rules for a multi-repo MkDocs setup:

---

# Contributing to the Documentation Hub

Thank you for helping improve our technical documentation! To maintain a consistent experience for our customers across all solutions, please follow these guidelines.

## 1. Where to Contribute
* **SME Content:** For technical guides, API specs, or solution-specific info, submit PRs to the **respective sub-repository**.
* **Site Infrastructure:** For changes to the theme, global navigation, plugins, or landing pages, submit PRs to the **Central Hub repository**.
  
## How to contribute

### Creating an issue

-   #### [Report a bug]

    __Something is not working?__ Report a bug in Material for MkDocs by
    creating an issue with a reproduction

-   #### [Report a docs issue]

    __Missing information in our docs?__ Report missing information or
    potential inconsistencies in our documentation

-   #### [Request a change]

    __Want to submit an idea?__ Propose a change, feature request, or
    suggest an improvement

-   #### [Ask a question]

    __Have a question or need help?__ Ask a question on our [discussion board]
    and get in touch with our community

### Contributing

-   #### [Add a translation]

    __Missing support for your language?__ Add missing translations for a new
    or already supported language

-   #### [Create a pull request]

    __Want to create a pull request?__ Learn how to create a comprehensive
    and useful pull request (PR)s

  [Report a bug]: docs/contributing/reporting-a-bug.md
  [Report a docs issue]: docs/contributing/reporting-a-docs-issue.md
  [Request a change]: docs/contributing/requesting-a-change.md
  [Ask a question]: https://github.com/squidfunk/mkdocs-material/discussions
  [Add a translation]: docs/contributing/adding-translations.md
  [Create a pull request]: docs/contributing/making-a-pull-request.md
  

## 2. Content Standards
* **Markdown Linting:** Ensure all files pass basic linting. Use standard Markdown headers (`#`, `##`) and avoid HTML tags where possible.
* **Front Matter:** Every new page must include metadata at the top:
    ```yaml
    ---
    authors: [git-handle]
    date: 2026-04-21
    description: Brief summary of this guide.
    ---
    ```
* **Image Assets:** Store images in an `assets/` or `images/` folder local to your SME repository. Use relative paths: `![Alt text](assets/diagram.png)`.

## 3. Navigation Rules
* **Sub-Navigation:** Each SME repository should maintain its own navigation in its local directory (if using the monorepo plugin).
* **Link Integrity:** Use **relative links** (`[link](../other-page.md)`) for internal content. Avoid absolute URLs to the production site to ensure links work in local previews.

## 4. Technical Guidelines
* **Admonitions:** Use MkDocs-Material callouts for emphasis:
    ```markdown
    !!! info "Pro Tip"
        Use these for helpful hints or warnings.
    ```
* **Code Blocks:** Always specify the language for syntax highlighting (e.g., ` ```yaml ` or ` ```bash `).

## 5. Branching & PR Process
1.  **Draft First:** Open a "Draft PR" if you are still working on the content to avoid premature reviews.
2.  **Local Preview:** Run `mkdocs serve` locally to verify that your changes render correctly within the site layout.
3.  **Peer Review:** All PRs require at least one approval from the designated SME Lead or a Platform Admin.
4.  **Squash and Merge:** We prefer squashing commits to keep the git history clean.

---

### Tips for Success
* **Be Concise:** Technical documentation should be "skimmable." Use bullet points and headers liberally.
* **Diagrams as Code:** If possible, use **Mermaid.js** (built into MkDocs-Material) for diagrams. This allows other contributors to edit diagrams without needing original image files.
* **The "One-Sentence" Rule:** Try to keep each paragraph focused on a single concept.

How do these rules align with the current workflow of your SME teams?