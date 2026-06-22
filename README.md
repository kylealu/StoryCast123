# StoryCast

A 3-page accessible microsite showcasing short audio and video travel stories.

## Project structure

```
storycast/
├── index.html              Home page — hero + featured story cards
├── about.html               About / Access page — mission + accessibility approach
├── story/
│   └── index.html           Story detail page — media, transcript, related stories
├── sass/
│   ├── _colors.scss         Color tokens
│   ├── _typography.scss     Font tokens
│   ├── _spacing.scss        Spacing tokens
│   └── main.scss            Main stylesheet (cascade layers, layout, BEM components)
├── css/
│   └── main.css             Compiled output — do not edit directly
├── assets/
│   ├── video/                Video story files
│   ├── audio/                Audio story files
│   └── transcripts/          .vtt caption files + plain-text transcripts
└── README.md
```

## How to run locally

1. No build step is required to view the site — open `index.html` directly in a browser, or use a tool like VS Code's "Live Server" extension for the best experience (handles relative paths correctly).
2. To edit styles, install Sass and watch the source files:
   ```
   npm install -g sass
   sass --watch sass/main.scss css/main.css
   ```
   Leave this running while you edit any `.scss` file — it will recompile `css/main.css` automatically.

## Accessibility checklist

- [x] Semantic HTML5 structure on every page (`<header>`, `<main>`, `<nav>`, `<article>`, `<figure>`, `<section>`, `<footer>`)
- [x] Logical heading hierarchy (single `<h1>` per page, nested `<h2>`/`<h3>` beneath it)
- [x] Skip-to-content link on every page for keyboard users
- [x] Visible focus outlines on all interactive elements (`:focus-visible`)
- [x] Video includes a `<track kind="captions">` pointing to a `.vtt` file
- [x] Audio and video stories both include a full text transcript, visible in the page (not hidden behind a download)
- [x] Color palette checked for WCAG AA contrast (4.5:1 minimum for body text)
- [x] All images include descriptive `alt` text
- [x] Site is fully operable via keyboard alone (Tab through all nav, links, and the `<details>` transcript toggle)
- [x] Container query implemented on the story card component — cards switch from stacked to side-by-side layout based on their own container width, independent of the viewport

## Design notes

- **Sass architecture**: organized using `@layer` (reset, base, layout, components, utilities) to control cascade order predictably, with BEM naming (`.story-card__title`, `.story-card__link--active`, etc.) for all components.
- **Responsive strategy**: CSS Grid for page-level layout (the featured story grid), Flexbox for component-level layout (header, footer, card internals), and one container query on `.story-card` for component-level responsiveness independent of the viewport.
- **Theme**: Travel storytelling — chosen as a simple, visual subject that naturally supports both video (scenery, motion) and audio (ambient sound) story formats.
