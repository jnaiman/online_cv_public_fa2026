# Online CV Template for IS445

This is a template for hosting an online CV/portfolio, with interactive visualizations, on your own GitHub Pages (`<your-username>.github.io`) site.  It is a resource for [IS445](https://uiuc-ischool-dataviz.github.io/is445_bcu_fall2026/) -- see the course page for more materials.

**[⬇️ Download the template as a zip file](https://github.com/jnaiman/online_cv_public_fa2026/archive/refs/heads/main.zip)**

Contents:
1. [Set up your site](#1-set-up-your-site)
1. [Run your site on your computer](#2-run-your-site-on-your-computer)
1. [Push your changes to GitHub](#3-push-your-changes-to-github)
1. [The files you will edit](#4-the-files-you-will-edit)
1. [Everything else (less important)](#5-everything-else-less-important)

---

## 1. Set up your site

### Create your github.io repository

Follow GitHub's [Pages quickstart](https://docs.github.com/en/pages/quickstart) to create a repository named **`<your-username>.github.io`** (for example, `jnaiman.github.io`).

### Get the template files

Pick **one** of the options below.

**Option A: download the zip**
1. [Download the zip file](https://github.com/jnaiman/online_cv_public_fa2026/archive/refs/heads/main.zip) and unzip it.  You'll get a folder called `online_cv_public_fa2026-main`.
1. Move **everything inside** that folder (not the folder itself) into your `<your-username>.github.io` repository:
   * **On your computer:** clone your github.io repository, copy the files into it, then [push](#3-push-your-changes-to-github).
   * **In the browser:** on your repository's GitHub page click **Add file → Upload files** and drag the files and folders in.  GitHub only accepts 100 files per upload and this template has a bit more than that, so upload in two batches (for example, the folders that start with `_` first, then everything else), committing after each.

**Option B: clone this repository** and copy its files (everything except the hidden `.git` folder) into your github.io repository.

### Check that GitHub Pages is on

In your repository go to **Settings → Pages** and make sure **Source** is "Deploy from a branch" with branch `main` and folder `/ (root)`.  After a few minutes your site will be live at `https://<your-username>.github.io` (you can watch it build under the **Actions** tab).

> You can edit your files right on GitHub and never install anything -- GitHub builds the site for you.  But it is **much** faster to see your changes if you run the site on your own computer (next section).

---

## 2. Run your site on your computer

### Install (once)

1. Install Ruby **3.x or 4.x** (see the course's installation instructions) and git.
1. In a Terminal/Anaconda Prompt, go into your github.io folder and run:
   ```
   bundle install
   ```

### Serve your site

```
bundle exec jekyll serve
```

Then open **http://localhost:4008** in your browser.  Refresh the page to see changes you've saved.

* For "live" reloading (the page refreshes itself) use `bundle exec jekyll serve -l`.  You can only live-reload one site at a time, otherwise you'll get a long and nebulous error.
* **If you change `_config.yml` you have to stop the server (`CTRL+C`) and start it again.** Every other file updates on its own.
* Stop the server with `CTRL+C`.

**Troubleshooting:** if `bundle install` or `bundle exec jekyll serve` fails (especially after you install a different version of Ruby), delete the file `Gemfile.lock` and run `bundle install` again.

---

## 3. Push your changes to GitHub

When you're happy with your changes, in the Terminal/Anaconda Prompt (make sure you have git installed!):

```
git pull               # ONLY if you have edited things online in your repo
git status             # see what changed
git add -A             # add all changes
git commit -m "message"
git push
```

After some build time (see the **Actions** tab) your live site updates.

> **Note:** if you have edited things online you'll get a merge warning when you push.  Download your repository's changes (`git pull`), merge (`git merge`), commit (`git commit -m "..."`) and push again.  It's easiest if you make all your changes locally instead of on GitHub.

---

## 4. The files you will edit

```
<your-username>.github.io/
├── _config.yml               <- PART 1 at the top: your name, title, links, etc.
├── about_me/                 <- everything about you
│   ├── about.md              <- the intro text on your About page
│   ├── programming-skills.yml
│   ├── other-skills.yml
│   ├── timeline.yml
│   └── remote_repos.yml      <- GitHub repos to show on your Projects page
├── projects/                 <- one markdown file per project
│   └── 1_Vega_lite_project.md
├── my_assets/                <- files your projects use
│   ├── json/                 <- vega-lite/Altair chart .json files
│   └── pngs/                 <- images & screenshots
└── python_notebooks/         <- "loose" notebooks (optional)
```

### `_config.yml`

This is the first file you'll modify.  It is split into two parts:

* **PART 1: YOUR SETTINGS** (the top) -- edit these:
  * `title` -- the title of your site (e.g. "[Last Name] Resume").
  * `description` -- say a little bit about yourself.
  * `baseurl` -- leave it as `""` if this is your main `<your-username>.github.io` site (this is where employers will "land").  If you are hosting the template in another repository, put that repository's name here (e.g. `"/my_cv"`).
  * `repository` -- your GitHub username.
  * `author` -- your name, a link to a picture of you, and the accounts you want shown as icons under your name.  Remove the `#` in front of an account to turn it on.
  * Want a **Blog** link in your navbar?  It's hidden by default -- comment out the `- pages/blog.html` line under `nav_exclude` in PART 2.
* **PART 2: ADVANCED SETTINGS** (the bottom) -- you generally don't need to touch these.  The one you might change is `exclude`: if you have other files stored in your github.io repository that shouldn't be part of your website, add them there.

Remember to restart `bundle exec jekyll serve` after changing this file!  (And no, it can't be renamed without the underscore -- `_config.yml` is the only name GitHub Pages looks for.)

### `about_me/about.md`

The introduction at the top of your **About** page.  Edit the text above the `<div class="row">` lines -- the skills and timeline below it come from the `.yml` files in the same folder.

### `about_me/programming-skills.yml` and `about_me/other-skills.yml`

Your programming skills and your other skills, each with a progress bar.  Each skill looks like:

```yaml
- name: Python          # name of the skill
  percentage: 90        # how full the bar is (0-100)
  level: Expert         # text shown next to the name
  color: danger         # bar color: primary, secondary, success, info, warning, danger, light or dark
```

The colors are defined in `_template/sass/_variables.scss`.  Leave `color:` empty for the default blue.

### `about_me/timeline.yml`

The timeline on your About page.  Each entry needs:

```yaml
- title: Student, Information Sciences   # job or degree
  from: 2024
  to: present
  description: A sentence or two about it.
```

This is **ORDER DEPENDENT** -- entries show up in the same order as the file, so put your most recent position on top if you want it first.

### `about_me/remote_repos.yml`

GitHub repositories to show as cards on your Projects page (after your project pages).  List the name at the end of each repository's URL, one per line:

```yaml
- my_cool_repo                                   # https://github.com/<you>/my_cool_repo
- UIUC-iSchool-DataViz/is445_bcu_fall2026        # a repository owned by someone else: owner/name
```

Each card's description and topic tags come from the repository's "About" section on GitHub and are filled in by the visitor's browser -- so on your own computer they may not show up if you are offline.

### `projects/`

This is where you'll spend most of your time: each markdown file in this folder becomes a project page and a card on your **Projects** page.  The template includes `1_Vega_lite_project.md`, a basic vega-lite example.

* Projects are listed in file-name order -- that's why the file starts with `1_`.  Name your next one `2_...md`, and so on.
* Each file starts with settings between `---` lines:
  ```yaml
  ---
  title: Vega Lite Example Project               # name shown on the card and page
  tools: [Python, HTML, vega-lite]               # tags shown on the card
  image: my_assets/pngs/cars.png                 # picture on the card
  description: A "showcase" project that uses vega-lite for interactive viz!
  custom_js:
    - vega.min
    - vega-lite.min
    - vega-embed.min
    - justcharts
  ---
  ```
* **Of vital importance!  If you are using vega-lite to make interactive plots, you MUST include the `custom_js` lines!!!**
* The rest of the file is written in markdown, plus `<vegachart>` tags for interactive visualizations:
  ```html
  <vegachart schema-url="{{ site.baseurl }}/my_assets/json/cars.json" style="width: 100%"></vegachart>
  ```

See the `_template/examples/projects/` folder for more examples (copy one into `projects/` to try it out).

### Extra page elements (carousels, buttons, videos, ...)

Want an image carousel, a YouTube video or a button in a project?  The folder **`_template/examples/elements/`** has an example of every page element the template supports.  Each file shows the code to copy, inside `{% raw %} ... {% endraw %}` -- copy just the part *between* those two lines into your project's `.md` file.

| Element | Example file | Code to copy into your page |
|---|---|---|
| Image carousel (slideshow) | `18-carousel.html` | see below |
| Button | `11-buttons.html` | `{% include elements/button.html link="https://github.com" text="GitHub" %}` |
| YouTube video | `19-videos.html` | `{% include elements/video.html id="aZNbUITN-mA" %}` (the `id` is the end of the video's YouTube URL) |
| Figure with a caption | `17-figures.html` | `{% include elements/figure.html image="https://bit.ly/2N69TKO" caption="The Ocean" %}` |
| Highlighted text | `03-highlight.html` | `{% include elements/highlight.html text="I am highlighted text." %}` |
| List of links / table of contents | `14-list-group.html`, `15-table-of-contents.html` | see the example files |
| GitHub gist | `10-github-gists.html` | `{% gist <your gist id> %}` |
| Headers, emphasis, links, lists, code, tables, task lists, ... | the other files | plain markdown/HTML -- just copy |

For example, a carousel of your own images (one image per line, between the `capture` lines):

```
{% capture carousel_images %}
{{ site.baseurl }}/my_assets/pngs/first_image.png
{{ site.baseurl }}/my_assets/pngs/second_image.png
{% endcapture %}
{% include elements/carousel.html %}
```

(Only one carousel per page works.)  The code behind each `{% include elements/... %}` is in `_template/includes/elements/`.

### `my_assets/`

Files your projects use: save your vega-lite/Altair chart `.json` files in `my_assets/json/` and screenshots/images in `my_assets/pngs/`.

### `python_notebooks/`

A place for "loose" Python notebooks.  Generally you'll link to notebooks in whatever repositories hold your analysis, but if you want to do something "quick and dirty" you can put a notebook here.  Notebooks in this folder are not built into your website.

---

## 5. Everything else (less important)

We won't go over these in detail -- they are listed here as reference (useful if you're building your own site with a different template but want to include Altair/vega-lite plots).

| File/folder | What it does |
|---|---|
| `README.md` | This file -- info for anybody who stumbles across the repository.  You don't need to modify it. |
| `Gemfile` | Tells Bundler which Ruby packages (gems) to install.  `bundle install` reads it and writes the exact versions it picked to `Gemfile.lock` (that file is specific to your computer and isn't uploaded to GitHub).  You don't need to modify it unless packages become incompatible with your version of Ruby/Jekyll. |
| `.gitignore` | Files git should ignore, like the built site (`_site/`) and `Gemfile.lock`. |
| `pages/` | The main pages of your site: `projects.html` (the Projects page), `blog.html`, `index.md` (the landing page), `tags.html`, `404.html` and `search.json`. |
| `_posts/` | Blog posts.  File names must start with the date: `YYYY-MM-DD-title.md`.  They're mostly markdown with settings (title, tags, etc.) at the top -- see `_template/examples/posts/` for examples.  The blog is hidden by default (see `_config.yml` above). |
| `assets/` | Files the template itself uses: JavaScript (including the vega-lite libraries in `assets/js`), CSS and the favicon.  Put your own files in `my_assets/` instead. |
| `_template/` | Everything that makes the site look and work the way it does -- you don't need to edit anything in here.  It contains the folders below. |
| `_template/layouts/` | Different layouts for different kinds of pages (`default.html`, `page.html`, `post.html`, ...). |
| `_template/includes/` | Pieces of pages, e.g. `_template/includes/projects/project-card.html` determines how each project card looks and `_template/includes/projects/index.html` the Projects page. |
| `_template/sass/` | The site's styling.  Colors are in `_template/sass/_variables.scss`. |
| `_template/plugins/` | Custom Jekyll plugins from the [4dcu.be template](https://github.com/4dcu-be/4dcu.be).  Note: GitHub Pages doesn't run custom plugins, so neither does this template (your interactive charts are drawn by `assets/js/justcharts.js` instead). |
| `_template/examples/` | Examples to look at for ideas once you've started building your own: `projects/` and `posts/` (copy one into `projects/` or `_posts/` to try it out), and `elements/` -- examples of page elements (carousels, buttons, videos, ...) you can use in your pages (see [Extra page elements](#extra-page-elements-carousels-buttons-videos-)).  These are not part of your site. |

---

## Sources

This is an amalgamation of [portfolYOU](https://github.com/YoussefRaafatNasry/portfolYOU) and [4dcu.be](https://github.com/4dcu-be/4dcu.be).

[portfolYOU](https://github.com/YoussefRaafatNasry/portfolYOU) was used for:
 * overall style, taking off a few elements -- Blog, About, Projects all are included here
 * also progress bars for skills are modified to contain words, not percentages

[4dcu.be](https://github.com/4dcu-be/4dcu.be)
 * vega-lite additions -- found in the `_template/plugins` folder and the vega-added things in `assets/js`

<details>
<summary>Old notes on how this template was created</summary>

1. Start by searching for Jeykll themes: https://github.com/topics/jekyll-theme
2. pick the following: https://github.com/YoussefRaafatNasry/portfolYOU
3. clone and follow the "Installation" instructions here: https://youssefraafatnasry.github.io/portfolYOU/docs/
4. Added port
5. remove Gemfile.lock if needed
trying to install with: bundle install --path ~/.gem
5. `bundle install` in directory

bundle exec jekyll serve --> without the l for live reload if something else is running?

NOTE!!! it is quite likely that you have to serve the site locally and/or delete _site before pushing for your changes to go live.  I AM NOT SURE.  Have to re-start after you do a change to the config.yml file

</details>
