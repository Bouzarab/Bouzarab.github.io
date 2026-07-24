source "https://rubygems.org"

# GitHub Pages ships a fixed gem set; using this locally keeps you
# in sync with what GitHub Pages will actually build.
gem "github-pages", group: :jekyll_plugins

# Windows / JRuby helpers (harmless on macOS/Linux)
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", "~> 2.0"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]
