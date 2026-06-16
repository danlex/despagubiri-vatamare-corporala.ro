source "https://rubygems.org"

# Jekyll static-site generator. We deploy via GitHub Actions
# (bundle exec jekyll build), so we use the standard Jekyll gem
# rather than the legacy `github-pages` wrapper, which pins an old
# Jekyll 3.x that does not run on modern Ruby.
gem "jekyll", "~> 4.3"

group :jekyll_plugins do
  gem "jekyll-sitemap"   # generates /sitemap.xml
  gem "jekyll-seo-tag"   # canonical, Open Graph, Twitter cards, JSON-LD org
  gem "jekyll-redirect-from"  # static redirect stubs for old (pre-rebuild) URLs
end

# Windows / JRuby timezone data (harmless elsewhere)
gem "tzinfo-data", platforms: [:mingw, :mswin, :x64_mingw, :jruby]
gem "wdm", "~> 0.1.1", platforms: [:mingw, :mswin, :x64_mingw]
