# AGENTS.md — Resume (Bokka Mohan Kiran)

## Source of Truth & Sync Rules
- `Resume.tex` is primary source. Keep derived artifacts (`Resume.md`, `Resume.odt`) synchronized when editing `.tex`.
- `guidelines.md` is the blueprint: 1 page limit, 1 column, ATS-optimized layout, zero typos.
- `measureGuide.md` provides empirical measurement blueprints, benchmarking scripts, and verification logs for bullet metrics.
- `projectUrl.md` dictates project priority order (top = most prominent). Maintain exact order in Projects section.
- `certifications.md` is the raw source; `Resume.tex` renders a formatted subset.
- Key Skills must strictly reflect tools used in listed projects. Drop unused skills if projects are removed.
- When modifying, adding, or reordering projects, update both `Resume.tex` and `Resume.md`.

## Build Commands
```sh
pdflatex Resume.tex
pdflatex CoverLetter.tex
```
- Variant builds: `pdflatex Resume_<variant>.tex` (`backend`, `cloud`, `devops`, `net`, `spinircle`, `tmp`, `vibe`).
- `*.aux`, `*.log`, `*.out`, and `prompt.md` are gitignored.

## Bullet & Formatting Rules
- Structure: Strictly 1 column, black text, white background. No progress bars, skill meters, or graphic templates.
- Icons: `\fa*` icons (`fontawesome5`) permitted ONLY in header line (email, phone, LinkedIn, GitHub).
- Limits: Maximum 3–4 bullet points per project/role.
- XYZ Formula: [Action Verb] + [Specific Task/Tool] + [Measured Impact]. Refer to `measureGuide.md` for proof.
- Action Verbs: Lead with strong verbs (Built, Automated, Deployed, Migrated, Reduced, Standardized).
- Accuracy: Do not fabricate metrics or repo features.
