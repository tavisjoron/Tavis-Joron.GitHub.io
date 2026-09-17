# Field Notes — blog

A plain HTML/CSS blog. No build step, no framework — just files.

## Structure

```
index.html              ← homepage, lists all posts
styles.css               ← shared styling
posts/
  post-template.html     ← copy this to start a new post
  welcome.html            ← example first post
```

## Writing a new post

1. Copy `posts/post-template.html` and rename it, e.g. `posts/october-garden-notes.html`.
2. Edit the `<title>`, the `<time>` tag (both the `datetime` attribute and the
   visible date), the `<h1>`, and the body text.
3. Open `index.html` and add a new `<li>` to the top of the `<ul class="post-list">`,
   copying the pattern of the existing entry — date, title linking to your new
   file, and a one-line summary.

That's the whole workflow. No database, no CMS login — you're editing text files.

## Publishing with GitHub Pages + your custom domain

1. Create a new GitHub repository and push these files to it (root of the repo,
   not a subfolder).
2. In the repo: **Settings → Pages** → under "Build and deployment", set
   **Source** to "Deploy from a branch", branch `main`, folder `/ (root)`.
3. Add a file named `CNAME` (no extension) at the root of the repo containing
   just your domain, e.g.:
   ```
   yourdomain.com
   ```
4. At your domain registrar, point DNS at GitHub Pages:
   - For an apex domain (`yourdomain.com`): add **A records** pointing to
     GitHub's IPs:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - For `www.yourdomain.com`: add a **CNAME record** pointing to
     `<your-github-username>.github.io`.
5. Back in **Settings → Pages**, enter your custom domain in the "Custom domain"
   field and save — this writes the `CNAME` file for you if you skipped step 3,
   and once DNS resolves, GitHub will issue a free HTTPS certificate
   automatically (can take up to 24 hours).

Once live, pushing a new post file + the updated `index.html` to `main` is all
it takes to publish — GitHub Pages rebuilds automatically within a minute or two.

## Customizing

- Colors and fonts are all defined as CSS variables at the top of `styles.css`.
- Site title and tagline are in the `<header class="masthead">` block —
  repeated at the top of every page, so update it in `index.html` and in
  `posts/post-template.html` if you change it.
