# Day 4 – Performance Optimization

React app demonstrating route-based code splitting, lazy loading, and render optimization.

## Features

- **Code Splitting** – `About` and `Dashboard` routes are split into separate JS chunks and are not part of the main bundle.
- **Lazy Loading** – `React.lazy()` + `Suspense` load each route's code only when the user navigates to it.
- **Render Optimization** – `StatsWidget` is wrapped in `React.memo`; `useMemo` avoids recalculating filtered data on every keystroke.
- **Bundle Analysis** – `rollup-plugin-visualizer` generates a visual report of chunk sizes after build.

## Tech Stack

React 18 · React Router · Vite · rollup-plugin-visualizer

## Getting Started

```bash
npm install
npm run dev
```

App runs at `http://localhost:5173`.

## Build & Analyze Bundle

```bash
npm run build
```

This creates a `dist/` folder and a `dist/stats.html` report. Open `stats.html` in a browser to see chunk sizes.

Sample build output:

```
dist/assets/index-*.js       ~5 kB   (main chunk)
dist/assets/vendor-*.js      ~163 kB (react, react-dom, react-router-dom)
dist/assets/About-*.js       ~0.6 kB (loaded only on /about)
dist/assets/Dashboard-*.js   ~1.3 kB (loaded only on /dashboard)
```

`About` and `Dashboard` are separate from the main and vendor chunks — confirming code splitting is working.

## Screenshots

> Add screenshots here after running `npm run dev` locally.

| Home | Dashboard |
|---|---|
| _screenshot-home.png_ | _screenshot-dashboard.png_ |

## Deployment (Vercel)

1. Push this project to GitHub (see below).
2. Go to [vercel.com](https://vercel.com) → **New Project** → import the GitHub repo.
3. Framework preset: **Vite**. Build command: `npm run build`. Output directory: `dist`.
4. Click **Deploy**.
5. Add the live Vercel URL below.

**Live URL:** _add after deployment_

## Push to GitHub

```bash
git init
git add .
git commit -m "Day 4: performance optimization - code splitting, lazy loading, memoization"
git branch -M main
git remote add origin <your-repo-url>
git push -u origin main
```

## Project Structure

```
src/
  components/
    Loader.jsx        # Suspense fallback
    StatsWidget.jsx    # memoized card component
  pages/
    Home.jsx           # eager-loaded
    About.jsx          # lazy-loaded
    Dashboard.jsx       # lazy-loaded
  App.jsx              # routes + Suspense
  main.jsx
```
"# debebe-kids-store" 
