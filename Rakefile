task :default => :preview

desc "rebuild the site and start the server"
task :preview do
  system "rm -rf _site"
  system "jekyll --server --auto"
end

namespace :post do
  desc "Create a new post and edit in Notepad++"
  task :new do
    system "ruby create.rb"
  end
end
 
desc "deploy site to Heroku and Github"
task :deploy do
  system "jekyll"
  system "git add _posts/* _site/*"
  system 'git commit -m "updated page"'
  system "git push dreamhost master"
end