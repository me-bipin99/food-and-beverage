# Ming Food & Beverages

## ⚙️ Requirements & Setup
Tech stack 
- **React**: ^18.3.1 / **React DOM**: ^18.3.1
- **React Router DOM**: ^7.1.1
- **Vite**: ^7.3.3 (with `@vitejs/plugin-react` ^4.3.1)
- **TypeScript**: ^5.5.3
- **Tailwind CSS**: ^3.4.1 (+ `postcss` ^8.4.35, `autoprefixer` ^10.4.18)
- **ESLint**: ^9.9.1 (+ `typescript-eslint` ^8.3.0)

**Node.js**: Vite 7 requires **Node.js 20.19+ or 22.12+** (Node 18 is not supported)

To install without version conflicts, use the exact versions pinned in `package-lock.json`:
```bash
npm ci        # clean install matching package-lock.json exactly
npm run dev   # start the dev server
```
If you don't have `package-lock.json` or intentionally want the latest matching `^` ranges instead, use `npm install` in place of `npm ci`.

## 📁 Project Structure (Current)
```
food-and-beverage/
├─ index.html                  # HTML entry point (Vite mounts #root here)
├─ src/
│  ├─ assets/
│  │  └─ images/                # Static images used across the site
│  │      ├─ home1.jpg, home1.png, home2.jpg   # Hero / home section images
│  │      ├─ blacktea.jpg, blacktea1.jpg, blacktea2.jpg
│  │      ├─ fryrice.jpg, jholmomo.jpg, 4385652.jpg, 2024-12-18.jpg
│  │      └─ ming1.png, minglogo.png            # Branding / logo
│  ├─ components/               # Re‑usable UI components
│  │   ├─ Navbar.tsx            # Navigation bar (state‑aware)
│  │   ├─ Hero.tsx              # Hero section with CTA
│  │   ├─ FeaturedItems.tsx     # Home‑page *Top Foods* preview (2 × 3 grid)
│  │   ├─ FullMenu.tsx          # Dedicated full‑menu page (search / filter / sort)
│  │   ├─ MenuItem.tsx          # Card for a single dish
│  │   ├─ CategoryFilter.tsx    # Category selector
│  │   ├─ SearchSort.tsx        # Search + sort controls
│  │   ├─ About.tsx             # About section
│  │   ├─ Story.tsx             # Brand story section
│  │   ├─ MomoPopup.tsx         # Promotional momo popup/modal Thursday special alert 
│  │   ├─ Preloader.tsx         # Initial loading screen
│  │   └─ Footer.tsx            # Footer with quick links
│  ├─ data/
│  │   └─ menuData.ts           # Static data: menuCategories, menuItems (name, image, description, price)
│  ├─ App.tsx                   # Root component – view router (`home` | `menu`)
│  ├─ main.tsx                  # Application entry point
│  ├─ index.css                 # Global styles / Tailwind directives
│  └─ vite-env.d.ts             # Vite/TypeScript environment types
├─ vite.config.ts               # Vite configuration (React + OXC)
├─ tailwind.config.js           # Tailwind CSS configuration
├─ postcss.config.js            # PostCSS configuration
├─ eslint.config.js             # ESLint configuration
├─ tsconfig.json / tsconfig.app.json / tsconfig.node.json   # TypeScript configs
├─ netlify.toml                 # Netlify deployment configuration
└─ package.json                 # Scripts & dependencies
```

## 🎯 Future Roadmap
- **Admin Dashboard** (planned) – a protected area where staff can:
  - Add, edit, delete menu items on‑the‑fly.
  - Re‑order categories.
  - Upload images (or provide URLs) for each dish.
  - Persist changes in **`localStorage`** for now (later replace with a proper backend).
- **Dynamic Menu Data** – `src/data/menuData.ts` now exposes helper functions:
  ```ts
  export const defaultMenuItems = [ /* all starter dishes */ ];
  export function getMenuItems(): MenuItem[];   // reads from localStorage or falls back to defaults
  export function setMenuItems(items: MenuItem[]): void; // writes to localStorage
  ```
  Components (`FeaturedItems`, `FullMenu`) import `getMenuItems()` instead of a static array, so any admin changes instantly reflect in the UI.
- **Authentication stub** – a simple “admin mode” toggle that could be expanded with JWT / OAuth later.
- **Styling polish** – glass‑morphism cards, subtle micro‑animations, dark‑mode support.

---
