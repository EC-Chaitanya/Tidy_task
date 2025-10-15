# 🚀 TidyTask - Local Setup Guide

A modern, playful, and animated multi-page website for a student-focused AI app with neurodiversity-friendly design.

---

## 📁 Project Structure

```
tidytask/
├── App.tsx                          # ⚠️ Main application component (ENTRYPOINT)
├── App.jsx                          # ⚠️ Duplicate (can be removed)
├── index.html                       # HTML entry point
├── package.json                     # Dependencies and scripts
├── vite.config.ts                   # Vite configuration
├── postcss.config.js                # PostCSS configuration for Tailwind
│
├── src/
│   └── main.tsx                     # Vite entry point (mounts App.tsx)
│
├── styles/
│   ├── globals.css                  # ✅ Tailwind V4 + TidyTask theme
│   └── main.css                     # Additional styles (if any)
│
├── components/
│   ├── Navbar.jsx                   # Navigation bar with animations
│   ├── Footer.jsx                   # Footer component
│   │
│   ├── pages/                       # All page components
│   │   ├── LandingPage.tsx          # Home page
│   │   ├── FeaturesPage.tsx         # Features showcase
│   │   ├── AboutPage.tsx            # About/mission page
│   │   ├── ContactPage.tsx          # Contact form page
│   │   └── DashboardPage.tsx        # Dashboard (after login)
│   │
│   ├── figma/
│   │   └── ImageWithFallback.tsx    # Protected: Image component
│   │
│   └── ui/                          # shadcn/ui components (44 components)
│       ├── button.tsx
│       ├── card.tsx
│       ├── input.tsx
│       └── ... (41 more components)
│
└── guidelines/                      # Documentation (not needed for running)
    ├── FINAL-FIXES.md
    ├── NAVBAR-FIX-COMPLETE.md
    └── ... (other docs)
```

---

## 📦 Required Dependencies

### Core Dependencies:
```json
{
  "react": "^18.x",
  "react-dom": "^18.x",
  "motion": "latest",              // Framer Motion (renamed)
  "lucide-react": "latest",        // Icons
  "recharts": "latest",            // Charts for dashboard
  "react-slick": "latest",         // Carousel
  "sonner": "^2.0.3",             // Toast notifications
  "class-variance-authority": "latest",
  "clsx": "latest",
  "tailwind-merge": "latest"
}
```

### Dev Dependencies:
```json
{
  "vite": "^5.x",
  "typescript": "^5.x",
  "@vitejs/plugin-react": "^4.x",
  "tailwindcss": "^4.x",          // Tailwind V4
  "postcss": "^8.x",
  "autoprefixer": "^10.x",
  "@types/react": "^18.x",
  "@types/react-dom": "^18.x"
}
```

---

## 🛠️ Setup Instructions

### Prerequisites:
- **Node.js** (v18 or higher) - [Download](https://nodejs.org/)
- **npm** (comes with Node.js) or **yarn** or **pnpm**
- A code editor (VS Code recommended)

---

### Step 1: Install Node.js

Check if Node.js is installed:
```bash
node --version
npm --version
```

If not installed, download from [nodejs.org](https://nodejs.org/)

---

### Step 2: Create package.json

If you don't have a `package.json`, create one with these dependencies:

```json
{
  "name": "tidytask",
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview",
    "lint": "eslint ."
  },
  "dependencies": {
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "motion": "^11.11.17",
    "lucide-react": "^0.468.0",
    "recharts": "^2.15.0",
    "react-slick": "^0.30.2",
    "slick-carousel": "^1.8.1",
    "sonner": "^2.0.3",
    "class-variance-authority": "^0.7.1",
    "clsx": "^2.1.1",
    "tailwind-merge": "^2.6.0",
    "@radix-ui/react-accordion": "^1.2.2",
    "@radix-ui/react-alert-dialog": "^1.1.4",
    "@radix-ui/react-aspect-ratio": "^1.1.1",
    "@radix-ui/react-avatar": "^1.1.2",
    "@radix-ui/react-checkbox": "^1.1.3",
    "@radix-ui/react-collapsible": "^1.1.2",
    "@radix-ui/react-dialog": "^1.1.4",
    "@radix-ui/react-dropdown-menu": "^2.1.4",
    "@radix-ui/react-label": "^2.1.1",
    "@radix-ui/react-popover": "^1.1.4",
    "@radix-ui/react-progress": "^1.1.1",
    "@radix-ui/react-radio-group": "^1.2.2",
    "@radix-ui/react-select": "^2.1.4",
    "@radix-ui/react-separator": "^1.1.1",
    "@radix-ui/react-slider": "^1.2.2",
    "@radix-ui/react-slot": "^1.1.1",
    "@radix-ui/react-switch": "^1.1.2",
    "@radix-ui/react-tabs": "^1.1.2",
    "@radix-ui/react-toast": "^1.2.4",
    "@radix-ui/react-tooltip": "^1.1.6"
  },
  "devDependencies": {
    "@types/react": "^18.3.18",
    "@types/react-dom": "^18.3.5",
    "@vitejs/plugin-react": "^4.3.4",
    "typescript": "~5.6.2",
    "vite": "^6.0.11",
    "tailwindcss": "^4.0.0",
    "postcss": "^8.5.1",
    "autoprefixer": "^10.4.20"
  }
}
```

---

### Step 3: Install Dependencies

Run one of these commands in your project folder:

```bash
# Using npm
npm install

# Using yarn
yarn install

# Using pnpm
pnpm install
```

This will install all dependencies from `package.json`.

---

### Step 4: Verify Configuration Files

Make sure you have these files:

#### **vite.config.ts**
```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import path from 'path'

export default defineConfig({
  plugins: [react()],
  resolve: {
    alias: {
      '@': path.resolve(__dirname, './'),
    },
  },
})
```

#### **postcss.config.js**
```javascript
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

#### **tsconfig.json** (if missing)
```json
{
  "compilerOptions": {
    "target": "ES2020",
    "useDefineForClassFields": true,
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true,
    "baseUrl": ".",
    "paths": {
      "@/*": ["./*"]
    }
  },
  "include": ["src", "components", "App.tsx"],
  "references": [{ "path": "./tsconfig.node.json" }]
}
```

---

### Step 5: Verify index.html

Make sure your `index.html` looks like this:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>TidyTask - AI-Powered Student Task Manager</title>
    
    <!-- Google Fonts - Montserrat & Poppins -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800&family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- Slick Carousel CSS (for react-slick) -->
    <link rel="stylesheet" type="text/css" href="https://cdnjs.cloudflare.com/ajax/libs/slick-carousel/1.8.1/slick.min.css"/>
    <link rel="stylesheet" type="text/css" href="https://cdnjs.cloudflare.com/ajax/libs/slick-carousel/1.8.1/slick-theme.min.css"/>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>
```

---

### Step 6: Verify src/main.tsx

Make sure your `src/main.tsx` exists:

```tsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from '../App.tsx'
import '../styles/globals.css'

ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
)
```

---

## ▶️ Running the Project

### Development Server:
```bash
npm run dev
```

This will start the development server. You should see:
```
VITE v6.x.x  ready in xxx ms

➜  Local:   http://localhost:5173/
➜  Network: use --host to expose
```

Open **http://localhost:5173/** in your browser!

---

### Build for Production:
```bash
npm run build
```

This creates an optimized build in the `dist/` folder.

---

### Preview Production Build:
```bash
npm run preview
```

This serves the production build locally.

---

## 🎨 Project Features

### Pages Included:
1. **Landing Page** (`/`) - Hero, features preview, testimonials, CTA
2. **Features Page** - Detailed feature cards with animations
3. **About Page** - Mission statement, team section
4. **Contact Page** - Animated contact form with gradient background
5. **Dashboard Page** - Task management, progress tracking, gamification

### Key Technologies:
- ⚛️ **React 18** - UI library
- ⚡ **Vite** - Build tool (super fast!)
- 🎨 **Tailwind CSS V4** - Styling
- ✨ **Motion (Framer Motion)** - Animations
- 🎯 **TypeScript + JavaScript** - Type safety (mixed)
- 🧩 **shadcn/ui** - 44 pre-built components
- 📊 **Recharts** - Charts for dashboard
- 🎠 **React Slick** - Carousel/slider

### Design Features:
- 🌈 Bright pastel gradients (blue, purple, aqua)
- ♿ Neurodiversity-friendly (ADHD-focused)
- 📱 Fully responsive (mobile + desktop)
- ✨ Smooth animations and transitions
- 🎯 Montserrat headlines + Poppins body text
- 🔵 Custom cursor follower (green-to-blue gradient)
- 🎨 Floating elements and particles

---

## 🐛 Common Issues & Solutions

### Issue 1: "Cannot find module 'motion/react'"
**Solution:** Install motion:
```bash
npm install motion
```

### Issue 2: Port 5173 already in use
**Solution:** Kill the process or use a different port:
```bash
npm run dev -- --port 3000
```

### Issue 3: TypeScript errors
**Solution:** The project uses mixed TS/JS. If you get errors, add:
```json
// tsconfig.json
{
  "compilerOptions": {
    "allowJs": true,
    "checkJs": false
  }
}
```

### Issue 4: Tailwind classes not working
**Solution:** Make sure `globals.css` is imported in `main.tsx`:
```tsx
import '../styles/globals.css'
```

### Issue 5: Fonts not loading
**Solution:** Check that Google Fonts links are in `index.html` (see Step 5)

---

## 📝 File Descriptions

### Root Files:
- **App.tsx** - Main application component with routing and state
- **index.html** - HTML entry point with fonts and meta tags
- **package.json** - Dependencies and npm scripts
- **vite.config.ts** - Vite build configuration
- **postcss.config.js** - PostCSS plugins (Tailwind)

### Source Files:
- **src/main.tsx** - Vite entry point, mounts React app

### Styles:
- **styles/globals.css** - Tailwind V4 config + TidyTask theme variables

### Components:
- **Navbar.jsx** - Top navigation with sliding indicator
- **Footer.jsx** - Footer with newsletter signup
- **pages/** - All page components (5 pages)
- **ui/** - shadcn/ui components (44 reusable components)

---

## 🚀 Next Steps

After running the project:

1. **Test the login flow:**
   - Click "Login" button → Opens Dashboard
   - Navbar updates with "Dashboard" link

2. **Test all pages:**
   - Home, Features, About, Contact, Dashboard
   - Check mobile responsiveness (resize browser)

3. **Test animations:**
   - Hover effects on buttons and cards
   - Page transitions
   - Cursor follower (green circle)
   - Navbar tab indicator slide

4. **Customize content:**
   - Edit pages in `components/pages/`
   - Update colors in `styles/globals.css`
   - Modify animations in components

---

## 📚 Useful Commands

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview

# Clean install (if issues)
rm -rf node_modules package-lock.json
npm install

# Check for outdated packages
npm outdated

# Update all packages
npm update
```

---

## 🎯 Quick Start (TL;DR)

```bash
# 1. Navigate to project folder
cd tidytask

# 2. Install dependencies
npm install

# 3. Start development server
npm run dev

# 4. Open browser
# Visit http://localhost:5173/
```

**That's it!** 🎉

---

## 🔧 Environment Requirements

| Tool | Minimum Version | Recommended |
|------|----------------|-------------|
| Node.js | v18.0.0 | v20.x or v22.x |
| npm | v9.0.0 | v10.x |
| Browser | Modern (2023+) | Chrome/Firefox/Safari latest |
| RAM | 4GB | 8GB+ |
| Disk Space | 500MB | 1GB+ |

---

## 📖 Additional Resources

### Documentation:
- [React Docs](https://react.dev/)
- [Vite Docs](https://vitejs.dev/)
- [Tailwind V4 Docs](https://tailwindcss.com/docs)
- [Motion Docs](https://motion.dev/)
- [shadcn/ui Docs](https://ui.shadcn.com/)

### Project Guidelines:
- `guidelines/FINAL-FIXES.md` - Latest bug fixes
- `guidelines/NAVBAR-FIX-COMPLETE.md` - Navbar implementation details

---

## ✅ Project Status

- ✅ Login button animation - **FIXED**
- ✅ Navbar tab indicator - **FIXED**
- ✅ Cursor follower - **FIXED**
- ✅ Text visibility - **FIXED**
- ✅ All pages working - **COMPLETE**
- ✅ Mobile responsive - **COMPLETE**
- ✅ Production ready - **YES**

---

## 🎊 You're All Set!

Your TidyTask project is ready to run! If you encounter any issues, check the "Common Issues" section above.

**Happy coding!** ✨🚀

---

**Version:** 1.0.0  
**Last Updated:** January 14, 2025  
**Status:** 🟢 Production Ready
