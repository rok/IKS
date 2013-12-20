task :default => :preview

desc "rebuild the site and start the server"
task :preview do
  system "rm -rf _site"
  system "jekyll serve watch"
end

namespace :post do
  desc "Create a new post"
  task :new do
    system "ruby create.rb"
  end
end
