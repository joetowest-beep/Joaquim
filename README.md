# 🚀 Publish with GitHub - GitHub Pages Site

A beautiful, responsive website about publishing projects with GitHub Pages. Built with React, Vite, and Tailwind CSS.

## 📦 Features

- 🎨 Beautiful dark-themed UI with gradient effects
- 🔌 Live GitHub API integration (connect to any user)
- 📱 Fully responsive design
- 📋 Code examples with copy-to-clipboard
- ❓ Interactive FAQ accordion
- 🌗 Dark/Light mode toggle

---

## 🚀 Deploy to GitHub Pages (Owner: Joaquim)

### Step 1: Create the Repository

1. Go to https://github.com/new
2. **Owner:** `Joaquim`
3. **Repository name:** `publish-with-github`
4. **Visibility:** Public
5. **Do NOT** initialize with README (we already have one)
6. Click **Create repository**

### Step 2: Push Source Code to `main`

```bash
git init
git add .
git commit -m "Initial commit - Publish with GitHub"
git branch -M main
git remote add origin https://github.com/Joaquim/publish-with-github.git
git push -u origin main
```

### Step 3: Build & Attach Binaries (dist folder) to `gh-pages` branch

The GitHub Actions workflow (`.github/workflows/deploy.yml`) will automatically:
1. Build the project (`npm run build`)
2. Commit the built files (binaries) to the `gh-pages` branch
3. Deploy them to GitHub Pages

**Just push to `main` and the workflow handles everything!**

#### Alternative: Manual Build & Deploy

If you prefer to build locally and attach the binaries yourself:

```bash
# Build the project
npm run build

# Create and switch to gh-pages branch
git checkout --orphan gh-pages

# Remove all tracked files, keep only dist/
git rm -rf .

# Copy dist contents to root
cp -r dist/* .
cp dist/.* . 2>/dev/null || true

# Remove the dist folder
rm -rf dist

# Commit the binaries
git add .
git commit -m "Deploy built binaries to gh-pages"

# Push gh-pages branch
git push origin gh-pages

# Switch back to main
git checkout main
```

### Step 4: Enable GitHub Pages

1. Go to your repo: `https://github.com/Joaquim/publish-with-github`
2. Click **Settings** → **Pages**
3. Under **"Build and deployment"**:
   - **Source:** Select **Deploy from a branch**
   - **Branch:** Select `gh-pages` → `/ (root)`
4. Click **Save**

### Step 5: Your Site is Live! 🎉

```
https://Joaquim.github.io/publish-with-github/
```

---

## 📁 What Gets Deployed (Binaries)

After building, the `dist/` folder contains:

```
dist/
├── index.html              # Main HTML file (3.22 kB)
└── assets/
    ├── index-XXXXX.css     # Compiled CSS (~41 kB)
    └── index-XXXXX.js      # Compiled JavaScript (~175 kB)
```

These are the **static binaries** that GitHub Pages serves directly. No build step needed on the server — they're pre-built and ready to go.

---

## 🔄 How Auto-Deploy Works

```
You push to main
       ↓
GitHub Actions triggers
       ↓
npm ci (install dependencies)
       ↓
npm run build (compile to dist/)
       ↓
dist/ binaries pushed to gh-pages branch
       ↓
GitHub Pages serves from gh-pages
       ↓
Site is live! 🎉
```

---

## 🛠️ Local Development

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

---

## 🌐 Custom Domain (Optional)

To use a custom domain:

1. Create a `CNAME` file in the `public/` folder:
   ```
   www.yourdomain.com
   ```

2. Configure DNS at your registrar:
   - **A records** pointing to GitHub's IPs:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`

3. In repo: **Settings** → **Pages** → Enter custom domain → ✅ Enforce HTTPS

---

## 📄 License

MIT
