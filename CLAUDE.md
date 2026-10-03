# UI notes for Claude

## Scope

The interactive prediction UI is the plain HTML, CSS, and JavaScript app in `index.html`, `style.css`, and `script.js`. `ML Project.html` is a separate project guide, not the UI entry point.

## Preserve the existing interface

- Treat the current light-mode design as the source of truth. Do not redesign the layout, spacing, typography, content, form, navigation, colors, or prediction flow unless the user explicitly asks.
- Make small, focused enhancements and avoid adding dependencies or introducing a frontend framework.
- Keep the page responsive. Preserve the existing breakpoints and check changes at mobile widths as well as desktop widths.
- Keep form field names and IDs stable. `script.js` uses them to validate values, build the API payload, handle errors, and render prediction states.

## Frontend structure

- `index.html` defines the header, prediction form, stress segmented control, live result panel, footer, and script/style links.
- `style.css` owns layout, responsive rules, design tokens, light/dark colors, focus treatment, and motion. The existing light theme is the default.
- `script.js` wires the form and theme toggle. It calls the API URL in `API_BASE` and persists the theme using `localStorage` under the `theme` key.
- Dark mode is selected by `data-theme="dark"` on the root HTML element. Keep light mode as the default for first-time visitors.

## Interaction and accessibility

- Preserve the prediction request and validation behavior when editing JavaScript.
- Keep the theme toggle keyboard accessible and maintain its accessible label and `aria-pressed` value.
- Preserve visible focus indicators and honor `prefers-reduced-motion` for non-essential animation.
- Avoid motion that could be distracting for a mental-health-related application.

## Local development

Install backend packages with `python3 -m pip install -r requirements.txt`. Run the API with `uvicorn main:app --host 127.0.0.1 --port 8001` and serve the project directory with `python3 -m http.server 8000`. Open `http://localhost:8000/`. Keep `API_BASE` in `script.js` aligned with the backend address.

## Change workflow

Before editing, inspect the relevant HTML, CSS, and JavaScript to understand the current behavior. Limit changes to files needed for the request. Afterward, check markup and JavaScript syntax when suitable tools are available, and verify that the default light appearance, theme persistence, responsive layout, and prediction workflow remain intact.
