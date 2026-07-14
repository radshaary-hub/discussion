# Open Discussion Hub 🚀

Open Discussion Hub is a production-ready, highly interactive community discussion platform designed for direct deployment to **GitHub Pages**. It operates as a high-performance Single Page Application (SPA) powered by React, TypeScript, Tailwind CSS, and Framer Motion.

## 🌟 Key Features

- 💬 **Nested Comments**: Interactive recursive conversation threads with real-time voting.
- 📊 **Polls**: Integrated voting widgets with live percentage bars and confetti effects.
- 🛡️ **Admin Dashboard**: Moderation queues, report audits, announcement publishers, and user ban controllers.
- ⚙️ **Dual-Mode Backend**: 
  - **Local Storage Engine**: Works immediately out-of-the-box (no database setup required).
  - **Supabase Integration**: Connects dynamically by dropping in environment variables.
- 📱 **Progressive Web App**: Offline capabilities, manifest caching, and custom SEO configurations.
- 🌓 **Rich Themes**: Sleek dark and light modes styled with premium HSL slates.

---

## 🛠️ Tech Stack

- **Framework**: [React 18](https://react.dev/) + [TypeScript](https://www.typescriptlang.org/)
- **Build Tool**: [Vite](https://vitejs.dev/)
- **Routing**: [React Router v6](https://reactrouter.com/) (configured with `HashRouter` for zero-configuration static page refreshes)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/)
- **Icons**: [Lucide Icons](https://lucide.dev/)
- **Animations**: [Framer Motion](https://www.framer.com/motion/)

---

## 💻 Local Development

### 1. Prerequisites
Ensure you have [Node.js (v18+)](https://nodejs.org/) installed on your local computer.

### 2. Installation
Clone the repository and install dependencies:
```bash
git clone https://github.com/your-username/open-discussion-hub.git
cd open-discussion-hub
npm install
```

### 3. Run Locally
Start the development server:
```bash
npm run dev
```
Open your browser and navigate to `http://localhost:5173/` (or the URL shown in your terminal).

### 4. Create Build Bundle
Validate compilation and build the static assets:
```bash
npm run build
```
Vite compiles and outputs the production bundle inside the `/dist` directory.

---

## 🚀 Deployment to GitHub Pages

The generated template contains an automated GitHub Actions workflow under `.github/workflows/deploy.yml` that compiles and deploys the platform on every push to the `main` branch.

### Step-by-Step Setup:
1. Create a repository on GitHub (e.g., `open-discussion-hub`).
2. Initialize git and push the generated code to your `main` branch:
   ```bash
   git init
   git add .
   git commit -m "Initialize Open Discussion Hub"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/open-discussion-hub.git
   git push -u origin main
   ```
3. In your GitHub repository, navigate to **Settings → Pages**.
4. Under **Build and deployment**, select **GitHub Actions** as the Source.
5. The workflow will automatically compile the Vite bundle and deploy it to a `gh-pages` branch.
6. Your website will be available shortly at:
   ```
   https://<your-github-username>.github.io/open-discussion-hub/
   ```

---

## 🗄️ Database Integration: Supabase / Firebase

By default, the platform boots up utilizing the **LocalStorage DB Engine**. To switch to a real persistent cloud database:

1. Create a project on [Supabase](https://supabase.com/) or [Firebase](https://firebase.google.com/).
2. Create a `.env` file in the root directory:
   ```env
   VITE_SUPABASE_URL=https://your-project-id.supabase.co
   VITE_SUPABASE_ANON_KEY=your-anon-api-key
   ```
3. Update `src/services/db.ts` to hook database calls into the Supabase client SDK:
   ```typescript
   import { createClient } from '@supabase/supabase-js';
   const supabase = createClient(
     import.meta.env.VITE_SUPABASE_URL,
     import.meta.env.VITE_SUPABASE_ANON_KEY
   );
   ```

---

## 🛠️ Troubleshooting

- **404 Errors on Refresh**: Since GitHub Pages is a static server, direct URL navigation (e.g., `/discussion/post-1`) can cause 404s. The platform solves this by default using `HashRouter` (`#/discussion/post-1`).
- **Base Path configuration**: If you rename the repository or use a custom domain, update `base: '/open-discussion-hub/'` inside `vite.config.ts`. If using a custom domain (e.g., `https://discussion.mydomain.com`), change `base` to `'/'`.

---

## 📄 License
Released under the [MIT License](LICENSE).
