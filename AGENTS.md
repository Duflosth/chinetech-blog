# Repository Guidelines

## Project Structure & Module Organization

This repository currently contains a single static page:

- `sino-tech-cyberpunk-blog.html` contains the HTML, embedded CSS, and a small inline script for reveal animations.
- `assets/` is referenced for `china-tech-cyberpunk-hero.png`; create this directory when adding or replacing image assets.
- No separate `src/`, `tests/`, or build output directories are present.

Keep related markup, styles, and interaction code close together unless the project grows enough to justify splitting files. Preserve the French content and navigation anchors unless the requested change explicitly updates them.

## Build, Test, and Development Commands

There is no package manager or build pipeline configured. Use direct browser checks for local development:

- `xdg-open sino-tech-cyberpunk-blog.html` opens the page directly.
- `python3 -m http.server 8000` serves the directory at `http://localhost:8000/` for browser testing.
- `npx html-validate sino-tech-cyberpunk-blog.html` can be used if Node tooling is available, but it is not required by the repository.

Do not add build tools, dependencies, or generated outputs unless they are needed for the requested change.

## Coding Style & Naming Conventions

Use two-space indentation for HTML, CSS, and JavaScript, matching the existing file. Prefer semantic HTML elements, accessible labels, and stable section IDs such as `#featured`, `#topics`, and `#subscribe`.

CSS class names use BEM-like patterns, for example `hero__content`, `button--cyan`, and `card--lead`. Continue using custom properties in `:root` for shared colors, typography, spacing, shadows, and radii.

## Testing Guidelines

No automated test suite exists yet. For each change, manually verify:

- The page loads without console errors.
- Responsive layouts work around mobile width, tablet width, and desktop width.
- Navigation anchors, form fields, and reveal animations still behave correctly.
- Referenced assets resolve successfully.

If tests are introduced later, place them in a clearly named `tests/` directory and document the runner here.

## Commit & Pull Request Guidelines

Git history is not available in this checkout, so no existing commit convention can be inferred. Use concise, imperative commit messages such as `Update hero article copy` or `Fix mobile card spacing`.

Pull requests should include a short summary, the reason for the change, screenshots for visual updates, and notes about manual browser checks performed.

## Agent-Specific Instructions

Keep edits focused on the static page unless asked to expand the project. Avoid broad rewrites, external dependencies, or new architecture for small content, style, or accessibility fixes.
