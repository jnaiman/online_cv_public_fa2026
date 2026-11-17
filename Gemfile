source "https://rubygems.org"

# This file tells Bundler which gems (Ruby packages) to install for this site.
# Install them with:      bundle install
# Run the site with:      bundle exec jekyll serve
#
# Tested with Ruby 3.3, 3.4 and 4.0.  If something breaks after you upgrade
# Ruby, delete Gemfile.lock and run "bundle install" again.

# GitHub Pages builds your site with Jekyll 3.10, so we use the same version
# locally.  (We don't use the "github-pages" gem itself because it cannot be
# installed on Ruby 4 yet.)
gem "jekyll", "~> 3.10.0"
gem "kramdown-parser-gfm"   # GitHub-flavored markdown, same as GitHub Pages

# Plugins this site uses (GitHub Pages runs these too).
group :jekyll_plugins do
  gem "jekyll-sitemap"            # makes sitemap.xml
  gem "jekyll-github-metadata"    # lets the Projects page show your GitHub repos
  gem "jekyll-gist"               # {% gist %} tag used in the _elements examples
end

# Lets "bundle exec jekyll serve" run a local web server (no longer built into Ruby).
gem "webrick"

# These used to come built into Ruby but were split out in Ruby 3.4 / 4.0.
# Jekyll and its plugins still need them, so we install them ourselves.
gem "base64"
gem "bigdecimal"
gem "csv"
gem "logger"
gem "ostruct"

# Windows does not include time zone files, so bundle them (harmless on Mac/Linux).
gem "tzinfo-data"
