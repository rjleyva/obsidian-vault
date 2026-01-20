# Obsidian Vault Backup

My knowledge management tool, serving as a prototype for the personal markdown
note-taking app I'll build when time permits.

## Overview

```mermaid
graph TD
    A[Sumi Knowledge Base] --> B[00-inbox]
    A --> C[01-references]
    A --> D[02-templates]
    A --> E[03-projects]
    A --> F[04-writing]

    style A fill:#f9f9f9,stroke:#333,stroke-width:2px
    style B fill:#e1f5fe
    style C fill:#f3e5f5
    style D fill:#e8f5e8
    style E fill:#fff3e0
    style F fill:#fce4ec
```

## Structure

Sumi uses a structured numbering system to organize knowledge:

### 00-inbox/

Raw incoming content, learning notes, and ideas to be processed

```mermaid
graph TD
    A[00-inbox/] --> B[New ideas & learning notes]
    A --> C[Raw incoming content]
    A --> D[Topics to process]

    style A fill:#e1f5fe,stroke:#333,stroke-width:2px
```

### 01-references/

Reference materials, documentation, and guides

```mermaid
graph TD
    A[01-references/] --> B[Technical references]
    A --> C[Framework documentation]
    A --> D[Best practices]

    style A fill:#f3e5f5,stroke:#333,stroke-width:2px
```

### 02-templates/

Reusable configurations and templates for development

```mermaid
graph TD
    A[02-templates/] --> B[ESLint configs]
    A --> C[Prettier setups]
    A --> D[TypeScript configurations]
    A --> E[Reusable templates]

    style A fill:#e8f5e8,stroke:#333,stroke-width:2px
```

### 03-projects/

Project-specific documentation and work-related content

```mermaid
graph TD
    A[03-projects/] --> B[salary.com projects]
    A --> C[CompAnalyst tools]
    A --> D[Pay equity management]
    A --> E[Compensation systems]

    style A fill:#fff3e0,stroke:#333,stroke-width:2px
```

### 04-writing/

Writing projects with drafts and published content

```mermaid
graph TD
    A[04-writing/] --> B[04-drafts]
    A --> C[16-published]

    B --> D[Writing in progress]
    C --> E[Published articles]

    B --> F[WezTerm setup guide]
    C --> G[CSS animation tips]

    style A fill:#fce4ec,stroke:#333,stroke-width:2px
    style B fill:#fce4ec,stroke:#666,stroke-width:1px
    style C fill:#fce4ec,stroke:#666,stroke-width:1px
```

## Workflow

1. **Capture** → Add new content to `00-inbox/`
2. **Process** → Move and refine content into appropriate sections
3. **Reference** → Use `01-references/` for quick lookups
4. **Apply** → Leverage `02-templates/` for consistent setups
5. **Document** → Track projects in `03-projects/`
6. **Share** → Publish writing through `04-writing/`

## File Naming Convention

Files use numbered prefixes for logical grouping and easy sorting:

- `01-` through `99-` for main categories
- Numbers increase with topic importance or chronological order
- Descriptive names follow the prefix for clarity

---

_Built for clarity, maintained with intention._
