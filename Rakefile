require 'html-proofer'
require 'yaml'

CONFIG   = YAML.load_file '_config.yml'
ROOT_URL = CONFIG.fetch 'url', ''
BASE_URL = CONFIG.fetch 'baseurl', ''
FULL_URL = File.join ROOT_URL, BASE_URL, '/'
DEST     = File.join '_site', BASE_URL

namespace :site do
  desc 'run default html-proofer tests'
  task :test do
    sh "bundle exec jekyll clean"
    sh "bundle exec jekyll build -d #{DEST}"

    opts = {
      allow_hash_href: true,
      assume_extension: true,
      swap_urls: { "#{FULL_URL}" => "/" }
    }
    HTMLProofer.check_directory('./_site', opts).run
  end
end