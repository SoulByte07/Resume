# AGENTS.md — Resume (Bokka Mohan Kiran)

## Source of truth

- `Resume.tex` is the primary source. `Resume.md` and `Resume.odt` are derived artifacts; keep them in sync when editing the .tex.
- `guidelines.md` is the blueprint — one page, one column, impact-first bullet points (XYZ formula), zero typos.
- `projectUrl.md` defines project priority order (top = most prominent). Match this order in the Projects section.

## Build

```sh
pdflatex Resume.tex
```

Build artifacts (`*.aux`, `*.log`, `*.out`) are gitignored.

## Key sync rules

- **Profile summary** mentions Jenkins and Lambda — if a project with those tools is removed, update the summary too.
- When adding/removing/reordering projects, update both `Resume.tex` and `Resume.md`.
- Certification source data is in `certifications.md`; `Resume.tex` contains the formatted subset.

## Style constraints

- Strictly one column, black text, white background, no icons/progress bars.
- Max 3–4 bullets per project. Lead with strong action verbs (Built, Automated, Deployed, Migrated).
- Each bullet: [Action Verb] + [Specific Task/Tool] + [Measured Impact].
- Never fabricate metrics or features not in the actual GitHub repo.
