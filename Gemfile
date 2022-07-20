source "https://rubygems.org"

gem "jekyll", "~> 4.2.2"


group :jekyll_plugins do
  gem "jekyll-sitemap", "~> 1.4"
    gem 'jekyll-seo-tag', '2.8.0'

end

# Windows

# The zoneinfo files are missing, so bundle the tzinfo-data gem and associated
# library.
install_if -> { RUBY_PLATFORM =~ %r!mingw|mswin|java! } do
  gem "tzinfo", "~> 1.2"
  gem "tzinfo-data"
end

# Performance-booster for watching directories and fix for livereload.
gem "wdm", "~> 0.1.0", :install_if => Gem.win_platform?
gem "webrick", "~> 1.7"
