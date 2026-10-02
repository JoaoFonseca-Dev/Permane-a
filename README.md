# Permaneça — Book Landing Page

A marketing landing page for *Permaneça*, a book by Tatiana Fonseca, built as a self-contained site with a WebGPU-first rendering pipeline and zero runtime dependencies.

**Live site:** https://permaneca-site.netlify.app

## Highlights

- **WebGPU → WebGL → CSS fallback.** The hero background renders through a custom WGSL shader on WebGPU, degrades to an equivalent GLSL shader on WebGL, and falls back to a pure-CSS gradient when neither API is available — detected and swapped at runtime.
- **GPU-driven particle system** in the accent sections, animated entirely on the GPU; the JS side only pushes elapsed time per frame.
- **No framework.** Vanilla ES modules, bundled and minified with esbuild.
- **Performance-conscious by design:** half-resolution offscreen rendering for the hero shader, device-pixel-ratio capped at 2x, `IntersectionObserver`-gated animation so nothing renders off-screen, a single shared `requestAnimationFrame` loop shared across every effect, and full respect for `prefers-reduced-motion`.
- **Accessible & SEO-ready:** semantic HTML, ARIA attributes on interactive components, Open Graph / Twitter Card metadata, and JSON-LD structured data (`schema.org/Book`).
- **Self-publishing testimonials:** a form that renders submitted testimonials straight onto the page — no backend required.
- **Zero-backend checkout:** every call to action deep-links into a pre-filled WhatsApp conversation, which is all a self-published book needs instead of a full payment stack.

## Stack

| Layer | Tech |
|---|---|
| Markup | Semantic HTML5, Open Graph, JSON-LD |
| Styling | Modern CSS (`@property`, `animation-timeline: scroll()`, `conic-gradient`) |
| Scripting | Vanilla JavaScript (ES modules) |
| Graphics | WebGPU (WGSL) · WebGL (GLSL) · CSS fallback |
| Build | esbuild + Sass |
| Hosting | Netlify, continuous deploy from this repository |

## Deployment

`index.html` in this repository is the production build: CSS and JavaScript inlined, images embedded as base64, with the `/video` folder referenced for the one media asset that stays external by design (inlining video as base64 isn't practical at that file size). Pushing to `main` triggers an automatic Netlify redeploy.

## Author

Built by [João Fonseca](https://github.com/JoaoFonseca-Dev).
