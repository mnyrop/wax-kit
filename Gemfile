source 'https://rubygems.org'

gem 'jekyll', '~> 4.3.2'


gem 'wax_theme', github: 'mnyrop/wax_theme', branch: 'main'
# gem 'wax_theme', path: 'wax_theme'

gem 'wax_cli', github: 'mnyrop/wax_cli', branch: 'main'
# gem 'wax_cli', path: 'wax_cli'

group :development, :test do 
  gem 'html-proofer'
  gem 'rake', '~> 13.0'
end

platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem 'tzinfo', '>= 1', '< 3'
  gem 'tzinfo-data'
  gem 'wdm', '~> 0.1.1'
end

