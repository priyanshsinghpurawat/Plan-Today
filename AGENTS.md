Always use:
- astro,tailwind-4-docs,web-design-guidelines these 3 skills for this project
- DESIGN.md for this project design

---

# Developer Reference & Coding Guidelines

## 🛠️ Build & Run Commands
- **Development Server**: `npm run dev` (starts on port 4321)
- **Production Build**: `npm run build` (outputs static pages to `dist/`)
- **Preview Build**: `npm run preview`
- **Lint Check**: `npx astro check`

## 📁 Key File Map
- `src/layouts/Layout.astro`: Base HTML shell, SEO metadata, and ambient mesh gradient canvas.
- `src/pages/index.astro`: Main page template holding the complete client-side reactive state logic (tasks database, focus timer, command palette, zen focus layout).
- `src/styles/global.css`: Core stylesheet linking Google Fonts (Inter & JetBrains Mono), mapping Tailwind v4 theme colors, custom border radii, custom typography tokens, and stacked elevation shadows.

## 🎨 Design Rules (Vercel Style Compliance)
- **Colors**: Use `#171717` (primary CTA/ink), `#ffffff` (canvas), `#fafafa` (canvas-soft background). Mesh gradients provide colors for alerts/glows.
- **Typography**: Display weights ceiling at `600` (sans font). Monospace (`font-mono` / Geist Mono) is for technical tags, timestamps, code snippets, and section eyebrows.
- **Headlines**: Sentence-case, period-terminated (e.g., `"Plan today. Play tomorrow."`).
- **Spacing**: Use standard Tailwind spacing numbers (`p-4`, `p-6`, `space-y-4`). For custom Vercel design tokens, use prefix `v-` spacing scale (e.g. `p-v-md` or `m-v-lg`) defined in `global.css` to prevent overriding Tailwind's default `max-w-2xl` / `3xl` width tokens.
- **Elevation**: Always use stacked shadows (`shadow-level-1` through `shadow-level-5` in `global.css`) instead of heavy single-blur drop-shadows.

## 🧠 State & Data Flow
- All task mutations and focus metric logs are computed in a single client-side `<script>` tag inside `index.astro`.
- Data is saved in the browser's `localStorage` (`plan-today-tasks-db`).
- Focus sessions accrue time directly to the linked task object if selected.
- Synthesized audio notifications are generated programmatically via the Web Audio API (no external file dependencies).