task :default => :preview

desc "rebuild the site and start the server"
task :preview do
  system "rm -rf _site"
  system "jekyll serve --watch"
end

desc "create 1st circular pdf"
task :pdf do
  system "cp en/1st-circular.textile ./1st-circular.textile"
  system "cp si/1-obvestilo.textile ./1-obvestilo.textile"
  system "sed -i 's/layout: default/layout: circular/g' ./1st-circular.textile"
  system "sed -i 's/layout: default/layout: circular/g' ./1-obvestilo.textile"
  system "jekyll build"
  system "sed -i 's/content-nc/content-circular/g' ./_site/1st-circular.html"
  system "sed -i 's/content-nc/content-circular/g' ./_site/1-obvestilo.html"
  system "wkhtmltopdf _site/1st-circular.html datoteke/1st-Circular.pdf"
  system "wkhtmltopdf _site/1-obvestilo.html datoteke/1-Obvestilo.pdf"
  system "rm 1-obvestilo.textile 1st-circular.textile"
end

namespace :post do
  desc "Create a new post"
  task :new do
    system "ruby create.rb"
  end
end
