source "https://rubygems.org"

# For local previews only (`bundle exec jekyll serve`); GitHub ignores this file
# and builds the live site with its own environment.
#
# These match the Jekyll + plugin versions GitHub Pages uses. We list them
# individually because the `github-pages` meta-gem doesn't support Ruby 4 yet.
gem "jekyll", "~> 3.10"
gem "kramdown-parser-gfm"

group :jekyll_plugins do
  gem "jekyll-remote-theme"
  gem "jekyll-sitemap"
  gem "jekyll-include-cache"
end

# Removed from Ruby's default gems in 3.4+, but still required by Jekyll 3.x
gem "base64"
gem "bigdecimal"
gem "csv"
gem "logger"
gem "webrick"

gem "tzinfo-data"
gem "wdm", "~> 0.1.0" if Gem.win_platform?
