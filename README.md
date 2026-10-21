# nettaofer.net

Personal website of Netta Ofer, design researcher. It's a plain static site (HTML + one CSS file), with no build step, no framework, and nothing to install. It's hosted free on GitHub Pages.

## What's where

```
index.html                 Home: navigation + project list
about.html                 Bio, artist statement, CV sections
publications.html          Publication list
teaching.html              Teaching, talks, mentorship
projects/*.html            One page per project
assets/style.css           All styling (colors and fonts are at the top)
assets/img/<project>/      Images for each project
assets/favicon.ico/.png    Browser tab icon
404.html                   "Page not found" page
.nojekyll                  Tells GitHub Pages to serve files as-is
```

## Editing

Every page is a normal HTML file you can edit in any text editor, or right on github.com (open the file, click the pencil icon, commit). Changes go live about a minute after you commit.

- **Change text:** edit the HTML file directly.
- **Add a publication:** in `publications.html`, copy an existing `<li>…</li>` block and change it.
- **Add a project:**
  1. Put images in a new folder `assets/img/<project-name>/`. Keep images under about 1800px wide; JPG for photos, WebP for animations.
  2. Copy an existing page in `projects/` to `projects/<project-name>.html` and edit it.
  3. In `index.html`, copy one `<a class="project-tile" …>` block and point it at the new page and cover image.
- **The menu** (About me / Publications / …) is repeated at the top of every page. If you add or rename a menu item, update it in every `.html` file. Find-and-replace across files in VS Code makes this quick.
- **Colors and fonts** are set at the top of `assets/style.css`.

### Preview on your computer (optional)

From this folder, run `python -m http.server`, then open http://localhost:8000.

## To do before going live

- [ ] **CV link.** The "CV" menu item currently points to the PDF hosted on the old Cargo site, which will stop working once Cargo is cancelled. Add a CV PDF to `assets/` (one **without** your home address and phone number, since this repo is public) and change the CV link in every page's menu to `assets/Netta_Ofer_CV.pdf` (`../assets/Netta_Ofer_CV.pdf` inside `projects/`).
- [ ] Look through each project page and check the text, image order, and captions.

## Hosting setup

### 1. Transfer the repository to Netta

The current owner does: **Settings → General → Danger Zone → Transfer ownership**, then enters Netta's GitHub username. Netta accepts the email invitation. GitHub redirects the old URL automatically.

### 2. Turn on GitHub Pages

In the repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: `main`, folder `/ (root)` → Save.**

The site appears at `https://<username>.github.io/<repo-name>/` within a minute or two. (If the repo is named exactly `<username>.github.io`, it's served at `https://<username>.github.io/` instead.)

### 3. Point nettaofer.net at it

Do these steps when you're ready to switch over from Cargo.

1. **(Recommended) Verify the domain with GitHub** so nobody else can claim it: your GitHub profile **Settings → Pages → Add a domain** → `nettaofer.net`. GitHub shows a TXT record to add at your domain registrar.
2. **At your domain registrar's DNS settings** (wherever nettaofer.net was bought), remove the old Cargo records and add:

   | Type  | Host / Name | Value                   |
   |-------|-------------|-------------------------|
   | A     | `@`         | `185.199.108.153`       |
   | A     | `@`         | `185.199.109.153`       |
   | A     | `@`         | `185.199.110.153`       |
   | A     | `@`         | `185.199.111.153`       |
   | AAAA  | `@`         | `2606:50c0:8000::153`   |
   | AAAA  | `@`         | `2606:50c0:8001::153`   |
   | AAAA  | `@`         | `2606:50c0:8002::153`   |
   | AAAA  | `@`         | `2606:50c0:8003::153`   |
   | CNAME | `www`       | `<username>.github.io`  |

3. In the repo: **Settings → Pages → Custom domain** → enter `nettaofer.net` → Save. GitHub adds a `CNAME` file to the repo for you.
4. DNS changes take anywhere from minutes to 24 hours to spread. Once the domain check passes, tick **Enforce HTTPS**.

GitHub's docs on this: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

> The `404.html` page uses root-relative links (`/…`), so it only displays correctly once the site is on the custom domain (or in a `<username>.github.io` repo). Every other page uses relative links and works at any address.

## Credits

Layout inspired by [navahaghighi.com](https://navahaghighi.com/). Fonts: [Hanken Grotesk](https://fonts.google.com/specimen/Hanken+Grotesk) and [IBM Plex Mono](https://fonts.google.com/specimen/IBM+Plex+Mono), both from Google Fonts.
