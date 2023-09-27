source 'https://rubygems.org'

gem 'jekyll', '~> 4.3.2'


gem 'wax-theme',  github: 'mnyrop/wax-theme',  branch: 'main'
gem 'wax-cli',    github: 'mnyrop/wax-cli',    branch: 'main'
gem 'wax_iiif',   github: 'minicomp/wax_iiif', branch: 'chore/wax_cli'

# gem 'wax-theme',  path: 'wax-theme'
# gem 'wax-cli',    path: 'wax-cli'
# gem 'wax_iiif',   path: 'wax_iiif'

group :development, :test do 
  gem 'html-proofer'
  gem 'rake', '~> 13.0'
end

platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem 'tzinfo', '>= 1', '< 3'
  gem 'tzinfo-data'
  gem 'wdm', '~> 0.1.1'
end

