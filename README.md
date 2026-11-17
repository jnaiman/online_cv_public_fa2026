# Online CV Templete for IS445

This is a resource for [IS445](https://uiuc-ischool-dataviz.github.io/is445_bcu_fall2026/).  It is a way to host an online CV with interactive visualizations.  See the course page for more materials.

# How to use this repo

## Download & install

 1. clone this repo or download the contents
 1. make sure you have Ruby (version 3.x or 4.x) *properly* installed (see the course's install instructions for this process)
 1. Install using `bundle install`
 1. Host locally with `bundle exec jekyll serve` or `bundle exec jekyll serve -l` (live reload)
 1. Modify files as needed (see sections below)

If `bundle install` or `bundle exec jekyll serve` fails after you change your Ruby version, delete `Gemfile.lock` and run `bundle install` again.

## Where things are

The files and folders **you will edit** are:

```
<your github username>.github.io/
├── _config.yml          <- PART 1 at the top: your name, title, links, etc.
├── about_me/            <- everything about you
│   ├── about.md
│   ├── programming-skills.yml
│   ├── other-skills.yml
│   ├── timeline.yml
│   └── remote_repos.yml <- GitHub repos to show on your Projects page
├── projects/            <- one markdown file per project page
│   └── 1_Vega_lite_project.md
├── my_assets/           <- files your projects use
│   ├── json/            <- vega-lite/Altair chart .json files
│   └── pngs/            <- images & screenshots
├── _posts/              <- blog posts (optional)
└── python_notebooks/    <- "loose" notebooks (optional)
```

Everything else (`pages/`, `_includes/`, `_layouts/`, `_sass/`, `_plugins/`, `assets/`, `Gemfile`, PART 2 of `_config.yml`) runs the site and generally does not need to be changed.  Folders starting with `_example_` hold examples you can copy from.

## General configurations

Edit info in **PART 1** (the top) of `_config.yml`:
 1. title, description, repository -- basic title and linking info
 1. baseurl -- in case you want to have it be a sub-page of your main github.io page
 1. author -- your name, picture, and the accounts shown as icons under your name

**PART 2** (the bottom) holds the advanced settings.  The one thing there you might change is `exclude`: add to it if you have other things stored in your github.io repo that shouldn't be built into your site.

Note: after changing `_config.yml` you have to stop (`CTRL+C`) and restart `bundle exec jekyll serve`.  The file must keep the name `_config.yml` (with the underscore) because that is the only name GitHub Pages looks for.

## About page

Everything for your About page is in the `about_me/` folder:
 1. `about.md` for your general introduction
 1. `programming-skills.yml` to update your programming skills list
 1. `other-skills.yml` to update other skills
 1. `timeline.yml` to update the timeline of your CV (shown in the same order as the file)

## Projects

Add project files in:
 * `projects/` to add project pages -- each markdown file in this folder becomes a project card on your Projects page
 * `about_me/remote_repos.yml` for links to your GitHub repositories -- list the end of each repo's URL (e.g. `my_repo` for `https://github.com/<you>/my_repo`), or `owner/repo` for a repo owned by someone else.  Each card's description and topic tags come from the repo's "About" section on GitHub and are loaded by the visitor's browser, so they may not show up if you are offline.

You can link both project pages and github repositories.  Github repos will autopopulate, pages allow you to provide more details.

By default, the project pages go first (ordered by file name, so start names with `1_`, `2_`, ...), but you can modify this if you want any github repos to show up first.

Each project file starts with a few settings between `---` lines, e.g.:

```
---
title: Vega Lite Example Project
tools: [Python, HTML, vega-lite]
image: my_assets/pngs/cars.png
description: This is a "showcase" project that uses vega-lite for interactive viz!
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---
```

Project layouts can be modified in `_includes/projects`.

See `_example_projects` folder for more examples from [portfolYOU](https://github.com/YoussefRaafatNasry/portfolYOU).

## Python notebooks

Generally, you will be linking notebooks that exist in other repositories that are doing analysis.  However for any "loose" notebooks, you can store them in the `python_notebooks` folder.  In theory you can do fancy local linking with it, but it hasn't been implemented yet.

## Altair-saved chart json's

By default these are saved in `my_assets/json/` and static images are saved in `my_assets/pngs/`.  See the example in `projects/1_Vega_lite_project.md`.

## Blog Posts

All blog posts will be posted by most recent time stamp -- please see the example for a properly formatted file name.

Add blog posts in:
 * `_posts` (see example)

You can see further examples in the `_example_posts` directory.


## Sources

This is an amalgamation of [portfolYOU](https://github.com/YoussefRaafatNasry/portfolYOU) and [4dcu.be](https://github.com/4dcu-be/4dcu.be).

[portfolYOU](https://github.com/YoussefRaafatNasry/portfolYOU) was used for:
 * overall style, taking off a few elements -- Blog, About, Projects all are included here
 * also progress bars for skills are modified to contain words, not percentages
 
[4dcu.be](https://github.com/4dcu-be/4dcu.be)
 * vega-lite additions -- found in the `_plugins` folder and the vega-added things in `assets/js`


# ------------- Old ramblings below -------------

# Info for how this was created

1. Start by searching for Jeykll themes: https://github.com/topics/jekyll-theme
2. pick the following: https://github.com/YoussefRaafatNasry/portfolYOU
3. clone and follow the "Installation" instructions here: https://youssefraafatnasry.github.io/portfolYOU/docs/
4. Added port
5. remove Gemfile.lock if needed
trying to install with: bundle install --path ~/.gem
5. `bundle install` in directory 


bundle exec jekyll serve --> without the l for live reload if something else is running?

NOTE!!! it is quite likely that you have to serve the site locally and/or delete _site before pushing for your changes to go live.  I AM NOT SURE.  Have to re-start after you do a change to the config.yml file


