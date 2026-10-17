# Stephen-Onochie.github.io

A React portfolio project that Stephen keeps as a showcase on his GitHub profile. The profile README in the `Stephen-Onochie/Stephen-Onochie` repo links here. **This is not Stephen's personal site.** His real site is stephenonochie.com and lives in that other repo, so don't make changes here that assume this repo is his primary web presence.

The project is a single-page React 18 + Vite 4 app styled with Tailwind 3 and animated with Framer Motion and react-three-fiber. It started from shaqdeff's open-source Portfolio-Template (MIT, see `MIT.md`), so some template leftovers remain, such as the `shaquille` package name, `shaq.png`, and project entries that link to shaqdeff's repos.

## Commands

- `npm ci` installs dependencies from the lockfile
- `npm run dev` starts the Vite dev server on http://localhost:5173
- `npm run build` writes the production build to `dist/`
- `npm run preview` serves `dist/` locally
- `npm run lint` runs ESLint. The repo has an `.eslintrc.cjs` for ESLint 8, and the lint baseline already has many errors (r3f props, prop-types, unused imports), so lint is not a gate right now.

`dist/` is committed from July 2024 and is stale. Don't commit rebuilt `dist/` output unless Stephen asks.

## Where content lives

Most copy changes only touch these files:

- `src/constants/index.js` holds nav links, services (About cards), technologies, experiences, and projects
- `src/assets/index.js` is the barrel for every image. **Any new image must be imported and exported here**, or the build fails with `"x" is not exported by "src/assets/index.js"`
- `src/components/*.jsx` has one component per section. Hero text is in `Hero.jsx`, and the About intro paragraph is in `About.jsx`
- `src/styles.js` holds shared Tailwind class strings (`styles.sectionHeadText` and others)
- `tailwind.config.js` holds the custom color names (`night`, `eerieBlack`, `taupe`, ...), breakpoints (`xs`, `xmd`, `3xl`), fonts, and the section background gradients (`bg-hero`, `bg-about`, `bg-tech`, `bg-experience`)
- `src/index.css` has the `@font-face` rules and global CSS

Sections are wrapped with `SectionWrapper(Component, 'anchor-id')` from `src/hoc`, which adds padding, stagger animation, and the `#anchor` used by the navbar. Section order is set in `src/App.jsx`.

## Gotchas

- `package.json` has `"type": "module"`, so config files use `export default` and must be `.js`. A `.cjs` file with ESM syntax makes Tailwind fail to load its config.
- The contact form uses EmailJS with keys hardcoded in `Contact.jsx`.
- Project and background images are 1.5 to 2.5 MB PNGs. Compress new images before adding them.
- The JS bundle is about 1.1 MB, mostly three.js. Vite's chunk-size warning is expected.

## Verifying changes

Run `npm run build` after every change. `npm run build && npm run preview` lets you check a visual change in a browser.
