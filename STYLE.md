A `STYLE.md` ensures that even with multiple SMEs contributing from different repositories, the final site feels like it was written by a single voice. For **MkDocs for Material**, this usually focuses on leveraging specific UI features like admonitions, content tabs, and icons.

---

# Style Guide: Technical Documentation

## 1. Voice and Tone
* **Active Voice:** Use active verbs. Say *"Install the package"* instead of *"The package should be installed."*
* **Direct & Concise:** Avoid "fluff" phrases like *"It is important to note that..."* Just state the fact.
* **User-Centric:** Focus on the "Why" and "How." Address the user as "you."

## 2. Structural Standards
### Headings
* Use **Sentence case** for headings (e.g., *Configure the cluster*, not *Configure The Cluster*).
* Avoid skipping levels (don't jump from `#` to `###`).
* Keep headings short and "scannable."

### Paragraphs & Lists
* Keep paragraphs to **3–5 sentences** maximum.
* Use **bulleted lists** for features or requirements.
* Use **numbered lists** for sequential steps.

## 3. MkDocs-Material Specifics
### Admonitions (Callouts)
Use these to highlight specific types of information. Avoid overusing them (no more than 2 per page).

```markdown
!!! note
    Use for neutral, supplementary information.

!!! success "Tip"
    Use for shortcuts or best practices.

!!! warning
    Use for actions that could cause data loss or service interruption.

!!! danger
    Use for critical security risks or hardware damage.
```

### Content Tabs
Use tabs to organize information that varies by context (e.g., OS, Cloud Provider, or Language) to reduce page length.

```markdown
=== "Linux"
    `sudo apt install nkp`
=== "macOS"
    `brew install nkp`
```

### Code Blocks
* **Always** specify the language for syntax highlighting.
* Use the `title` attribute for configuration files:
    ```yaml title="gitops/flux-config.yaml"
    apiVersion: source.toolkit.fluxcd.io/v1
    ...
    ```

## 4. Visuals & Media
* **Alt Text:** Every image must have descriptive `alt` text for accessibility.
* **Diagrams as Code:** Use **Mermaid** blocks for flowcharts or sequence diagrams. This ensures they are searchable and easy for any SME to edit.
    ```mermaid
    graph LR
      A[SME Repo] --> B(GitHub Action);
      B --> C{Central Hub};
    ```

## 5. Formatting Conventions
* **Bold:** Use for UI elements, buttons, and field names (e.g., Click **Submit**).
* **Italics:** Use for new terms or file paths (e.g., Open the *config.json* file).
* **Monospace:** Use for commands, variables, and code snippets (e.g., Set `NODE_ENV` to `production`).

---

### Pro-Tip: The "Glance" Test
A reader should be able to understand the **intent** and **outcome** of a page within 5 seconds of scrolling. If a page is a wall of text, break it up with headers, images, or admonitions.

How does this style align with your current internal documentation standards?