source 'https://rubygems.org'

gem 'jekyll', '~> 4.3.2'

# gem 'wax_theme'
gem 'wax_theme', github: 'mnyrop/wax-v2-theme', branch: 'main'
# gem 'wax_theme', path: 'wax_theme'

# gem 'wax_tasks'
gem 'wax_tasks', github: 'minicomp/wax_tasks', branch: 'bug/jekyll-src-dir-92'
# gem 'wax_tasks', path: 'wax_tasks'

group :jekyll_plugins do
  gem 'jekyll-feed', '~> 0.12'
end

platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem 'tzinfo', '>= 1', '< 3'
  gem 'tzinfo-data'
  gem 'wdm', '~> 0.1.1'
end

