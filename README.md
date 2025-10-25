# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default tseslint.config([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...

      // Remove tseslint.configs.recommended and replace with this
      ...tseslint.configs.recommendedTypeChecked,
      // Alternatively, use this for stricter rules
      ...tseslint.configs.strictTypeChecked,
      // Optionally, add this for stylistic rules
      ...tseslint.configs.stylisticTypeChecked,

      // Other configs...
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x'
import reactDom from 'eslint-plugin-react-dom'

export default tseslint.config([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Other configs...
      // Enable lint rules for React
      reactX.configs['recommended-typescript'],
      // Enable lint rules for React DOM
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
])
```






/* Mostly Viewed ticker - standalone styles (no reliance on Services.css) */
.mv-wrapper {
  width: 85%;
  margin: 10px auto 0 auto; /* centered just below navbar */
  background: transparent;
}

.mv-title {
  font-size: 18px;
  font-weight: 700;
  color: #961766;
  margin: 0 0 8px 4px;
}

/* Ticker viewport */
.mv-ticker {
  position: relative;
  overflow: hidden; /* clip to viewport */
  height: 140px; /* adjustable */
}

/* Scrolling track */
.mv-track {
  display: flex;
  gap: 16px; /* slight spacing between cards */
  width: max-content;
  animation: mv-scroll 28s linear infinite; /* moderate speed */
}

/* Pause on hover */
.mv-ticker:hover .mv-track {
  animation-play-state: paused;
}

/* Each visible card */
.mv-item {
  flex: 0 0 auto; /* width is content-based */
}

/* Card styling */
.mv-card {
  width: 240px; /* 3–5 visible depending on viewport */
  height: 100%;
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.08);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}

/* Image fills most of the card */
.mv-img {
  width: 100%;
  height: 100%;
  max-height: 110px; /* leave room for optional title */
  object-fit: cover; /* keep aspect while filling */
  object-position: center; /* avoid cropping faces when possible */
  display: block;
}

/* Optional small title */
.mv-desc {
  font-size: 12px;
  font-weight: 600;
  color: #333;
  text-align: center;
  padding: 6px 8px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

/* Link reset */
.mv-link {
  text-decoration: none;
  color: inherit;
}

/* Animation from right to left */
@keyframes mv-scroll {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}

/* Responsiveness */
@media (max-width: 1024px) {
  .mv-card { width: 220px; }
  .mv-ticker { height: 130px; }
  .mv-img { max-height: 100px; }
}

@media (max-width: 768px) {
  .mv-wrapper { width: 90%; }
  .mv-card { width: 200px; }
  .mv-ticker { height: 125px; }
  .mv-img { max-height: 96px; }
}

@media (max-width: 480px) {
  .mv-card { width: 180px; }
  .mv-ticker { height: 120px; }
  .mv-img { max-height: 90px; }
}
