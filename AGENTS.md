# AGENTS.md — Statistics Wiki

## Purpose
Build an extensible Traditional Chinese statistics knowledge base. New articles must follow `templates/article-template.md` and retain a consistent modern dark dashboard design.

## Stack
Static HTML, CSS, vanilla JavaScript, Markdown, marked.js, DOMPurify, MathJax and GitHub Pages. No backend or framework. Use relative paths for GitHub Pages subdirectory hosting.

## Visual rules
Dark navy `#0B1120`, sidebar `#111827`, cards `#1E293B`, primary accent `#6366F1`, secondary accent `#06B6D4`, text `#F8FAFC`, muted text `#94A3B8`. Reuse CSS variables, rounded cards, responsive navigation and accessible focus states. Do not redesign unrelated pages.

## Directory conventions
- `index.html`: application shell
- `css/style.css`: shared styling
- `js/main.js`: routing, index, search and Markdown rendering
- `data/articles.json`: article registry
- `content/inference/`, `content/regression/`, `content/survival/`, `content/evaluation/`: Markdown articles
- `templates/article-template.md`: mandatory content structure

File names are lowercase English kebab-case, e.g. `cox-proportional-hazards.md`.

## Article contract
Every article has YAML front matter with `title`, `description`, `category`, `tags`, `order`, followed by eight sections in order: Overview, Definition, Formula, Assumptions, Example, Code, Interpretation, Common Mistakes. Write Traditional Chinese by default, retaining English technical terms. Define notation, distinguish assumptions, and label hypothetical examples. Use `$...$` and `$$...$$` for math. SAS/R code must be syntactically plausible; never claim execution without testing. Never invent real outputs or causal conclusions.

## Adding a new article
1. Read `AGENTS.md`, `templates/article-template.md`, `data/articles.json` and one existing article.
2. Choose an existing category, or ask before adding a new category.
3. Create `content/<category>/<kebab-case-title>.md` with front matter and all eight sections.
4. Register a unique `id`, correct `path`, `category`, `title`, `description`, `tags`, and `order` in `data/articles.json`.
5. Do not hardcode a new page in HTML or JS. Navigation and search must use the registry.
6. Check mathematical correctness, code syntax, links, Markdown, MathJax, mobile layout and GitHub Pages paths.
7. Report files changed and which tests were actually run.

## Editing rules
Read before modifying; make minimal targeted edits, preserve valid content, keep registry synchronized, and do not modify unrelated files. Markdown is untrusted: sanitize rendered HTML with DOMPurify. Use safe DOM APIs for metadata, and validate article paths against the registry. Report any unverified claims or failed checks.

## Definition of done
Article is indexed and discoverable, eight headings present, math and code readable, links work, responsive layout preserved, and no unrelated content damaged. Never claim deployment or testing without verification.
