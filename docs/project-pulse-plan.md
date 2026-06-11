# Project Pulse — Implementation Plan

## Summary
Project Pulse is a lightweight dashboard showing health and progress metrics for projects. Deliver a static app (HTML/CSS/JSON) wired for easy extension and local debugging via .vscode/launch.json. Primary deliverables: app/index.html, app/styles.css, app/project-data.json, and .vscode/launch.json.

## Goals
- Provide a clear, extensible dashboard layout.
- Ship data-driven UI using project-data.json as source.
- Support local debug/run configurations for developers.
- Separate Designer (visual/UX) and Coder (implementation/data/automation) responsibilities.

## Ordered implementation steps
1. Project scaffolding and debug config
   - Create docs and app folders. Add .vscode/launch.json for local preview.
   - Files: .vscode/launch.json
   - Dependencies: none
   - Validation: VS Code can launch a simple static server or open index.html.

2. Data model and sample data
   - Define JSON schema for project entries and metrics. Populate app/project-data.json with representative data (2–5 projects, varied statuses).
   - Files: app/project-data.json
   - Dependencies: step 1
   - Validation: JSON validates against schema; dashboard reads and renders entries.

3. Core layout and markup
   - Build responsive HTML structure for header, filters, project cards, aggregates, and timeline/mini-charts.
   - Files: app/index.html
   - Dependencies: steps 1–2
   - Validation: Structure renders with sample data; accessible headings and ARIA where appropriate.

4. Styling and responsive design
   - Implement visual design, theming, spacing, colors, typography in app/styles.css.
   - Files: app/styles.css
   - Dependencies: step 3
   - Validation: Matches design intent across desktop and mobile breakpoints, good contrast.

5. Data binding and interactivity
   - Add minimal vanilla JS (inline or small separate file) to fetch app/project-data.json, render project list, apply filters/sorting, and show aggregate metrics. Keep code modular for future refactor.
   - Files: app/index.html (or app/scripts.js if created)
   - Dependencies: steps 2–4
   - Validation: Filtering and sorting behave as expected; metrics update when filters apply.

6. Small visual polish & accessibility
   - Add keyboard focus styles, semantic HTML, labels for interactive elements, alt text.
   - Files: app/index.html, app/styles.css
   - Dependencies: steps 3–5
   - Validation: Pass basic Lighthouse/accessibility checks for contrast and semantics.

7. Documentation & README
   - Add docs/project-pulse-plan.md (this file), and update README with run instructions and how to extend project-data.json.
   - Files: docs/project-pulse-plan.md, README.md (if editing)
   - Dependencies: steps 1–6
   - Validation: Developer can run and extend the project easily.

## File assignments (per step)
- Step 1: .vscode/launch.json
- Step 2: app/project-data.json
- Step 3: app/index.html
- Step 4: app/styles.css
- Step 5: app/index.html (scripts inline) or app/scripts.js (optional)
- Step 6: app/index.html, app/styles.css
- Step 7: docs/project-pulse-plan.md, README.md (optional)

(Per your request, included files: app/index.html, app/styles.css, app/project-data.json, .vscode/launch.json.)

## Designer responsibilities
- Create visual specs: color palette, typography scale, spacing, component states.
- Produce simple wireframe / final mock for desktop and mobile.
- Provide copy for labels, metric names, and empty-state messaging.
- Decide highlight priorities (which metrics/visuals are prominent).
- Review accessibility requirements: contrast targets and focus order.

## Coder responsibilities
- Implement scaffolding, debug configuration, and the static files.
- Define and validate JSON schema for project-data.json.
- Implement responsive HTML and CSS consistent with Designer specs.
- Implement data fetching, rendering, filtering, sorting, and small interactions.
- Add lightweight accessibility enhancements and unit/manual validation steps.
- Document data schema and extension points.

## Dependencies
- None external required for core static implementation. If adding charts, choose a small library (e.g., Chart.js) — note additional dependency and bundle impact.
- VS Code for .vscode/launch.json integrability (or any static file server).
- Browser for testing (Chrome/Firefox). Optional: Lighthouse for accessibility checks.

## Work that can run in parallel
- Designer: finalize visual spec and copy.
- Coder: implement scaffolding (.vscode, folders) and JSON schema + sample data.
- Coder: start HTML skeleton and basic CSS variables while Designer finishes visuals (use placeholders).
Parallel safe because placeholders can be swapped with final assets.

## Work that must run sequentially
- Styling polish depends on completed HTML skeleton.
- Data-driven interactivity depends on finalized JSON schema and sample data.
- Accessibility pass after markup & styles are stable.

## Edge cases & risks to handle
- Empty dataset: show friendly empty state with CTA to add projects.
- Large number of projects: implement simple pagination or virtualized list if growth is expected.
- Missing fields in project-data.json: render fallbacks (e.g., "—" for missing dates).
- Timezone handling for dates/timestamps.
- Color contrast failing for user-chosen themes.
- Mobile performance if heavy visuals introduced.

## Validation expectations
- Functional:
  - app/index.html loads and renders sample projects from app/project-data.json without server-side code.
  - Filters and sorting change visible results and update aggregate metrics instantly.
- Visual:
  - Layout matches Designer mock at desktop and mobile breakpoints.
  - Contrast ratio >= 4.5:1 for body text.
- Accessibility:
  - Page has logical heading order; interactive elements reachable by keyboard.
  - No critical Lighthouse a11y errors.
- Developer experience:
  - .vscode/launch.json enables preview or simple debugging session (document steps in README).
  - JSON schema documented and example data present.

## Open questions / decisions
- Should JS be inline in index.html or separated into app/scripts.js? (Recommend separate file for clarity.)
- Are charts required now or later? If yes, pick a lightweight chart lib and add to dependencies.
- Expected maximum projects count to guide pagination strategy.
- Any authentication or data refresh requirements (live updates)?

## Deliverables checklist
- [ ] .vscode/launch.json
- [ ] app/project-data.json (schema + sample)
- [ ] app/index.html (markup + minimal scripts)
- [ ] app/styles.css (responsive styles)
- [ ] docs/project-pulse-plan.md (this plan)
- [ ] README or run instructions

## Validation steps (concrete)
1. Open app/index.html in browser (or use .vscode launch). It should render the dashboard.
2. Run basic Lighthouse checks for accessibility and performance.
3. Manually test filters, sorting, and empty dataset behavior.
4. Validate JSON against schema (simple JSON Schema or manual checks).

## Next immediate actions (short)
- Designer: supply color palette, typography, and final mock for desktop + mobile.
- Coder: scaffold repo folders, add .vscode/launch.json, create project-data.json with schema and sample data, implement index.html skeleton and a minimal styles.css.

