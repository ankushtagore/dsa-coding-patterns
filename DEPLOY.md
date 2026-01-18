# 🚀 How to Deploy Your DSA Course to GitHub

Your local repository is already initialized and committed! Follow these simple steps to host it on GitHub as a professional documentation site.

## 1. Create a New Repository on GitHub
1. Go to [GitHub - Create New Repository](https://github.com/new).
2. Name it `dsa-coding-patterns`.
3. Keep it **Public**.
4. **Do not** initialize it with a README, license, or gitignore (we already have them!).
5. Click **Create repository**.

## 2. Push Your Local Code to GitHub
Open your terminal in the `dsa-coding-patterns` folder and run:

```bash
# Add your GitHub repo as a remote
git remote add origin https://github.com/YOUR_USERNAME/dsa-coding-patterns.git

# Rename branch to main (if not already)
git branch -M main

# Push your code
git push -u origin main
```

*(Note: Replace `YOUR_USERNAME` with your actual GitHub username.)*

## 3. Enable GitHub Pages (Deployment)
1. In your GitHub repository, go to **Settings** (tab at the top).
2. Click on **Pages** in the left sidebar.
3. Under **Build and deployment > Branch**, select `main` and `/ (root)`.
4. Click **Save**.
5. Wait about 30-60 seconds. A link will appear at the top: *"Your site is live at ..."*

## 4. Explore Your New Site!
Your documentation is now hosted! It is:
- ✅ **Searchable**: Use the search bar to find any pattern or problem.
- ✅ **Clean**: Beautifully rendered using Docsify.
- ✅ **Interactive**: Copy code buttons and highlighted syntax for Python, JS, and Go.

---

### 🎨 Customizing the Site
- To change the theme, edit `index.html`.
- To update the navigation, edit `_sidebar.md`.
- To add more patterns, create a folder/README and add it to `_sidebar.md`.

**Happy Coding! 🚀**
