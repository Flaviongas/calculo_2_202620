# AGENTS.md

Quarto source for a Spanish-language Cálculo 2 course (author: Flavio Jara L.). Each numbered directory (`1/`, `2/`, ...) is one class with a `class.qmd`.

## Build & render

- Render a class from repo root: `quarto render N/class.qmd`. Generates `N/class.html` + `N/class_files/`.
- If you edit a `class.qmd`, re-render and commit the output (`class.html` + `class_files/`). The deploy workflow only `git pull`s the server and serves the committed HTML; there is no build step in CI and no `.gitignore`.

## Conventions

- **YAML header:** for slide decks copy the block in `header.yaml` (revealjs, `transition: zoom`, `katex`, small-font `<style>`); do not change format options. Plain HTML pages use `format: html` instead (see `1/class.qmd`).
- **Slide body style:** one `## Ejercicio N` slide per exercise; a bare `##` (empty heading) continues to the next slide; prose explains each step before the math in `$$ ... $$`.
- **No tables or emojis** in lesson content (convert tables from source material into prose).
- Content is written in Spanish.

## Verifying math answers

Bash rules deny `py*` commands directly; run Python through a temp script under nix-shell:

```
nix-shell -p python3Packages.sympy --run "python3 /tmp/opencode/verify.py"
```