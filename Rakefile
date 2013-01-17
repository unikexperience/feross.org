require 'rubygems'
require 'rake'

#
# Compile
#

desc "Compile everything"
task :compile do
  sh "compass compile"
  sh "jekyll"
end

#
# Watch & continuously compile
#

desc "Watch-compile jekyll site"
task :jekyll do
  sh "jekyll --auto --server"
end

desc "Watch-compile SCSS with Compass"
task :compass do
  sh "compass watch"
end


#
# Deploy
#

desc "Deploy site"
task :publish do
  sh "rm -rf _site js/compiled css/compiled"
  sh "compass compile --output-style compressed"
  sh "jekyll --lsi"
  sh "rsync -r -a -v -e \"ssh -l feross -p 44444\" --delete _site nginx.conf _server future:/home/feross/www/feross.org/"
end