task :default => :preview

desc "rebuild the site and start the server"
task :preview do
  system "rm -rf _site"
  system "jekyll serve --watch"
end

desc "create 1st circular pdf"
task :pdf do
  system "cp en/1st-circular.textile ./1en.textile"
  system "cp si/1-obvestilo.textile ./1si.textile"
  system "sed -i 's/layout: default/layout: circular/g' ./1en.textile"
  system "sed -i 's/layout: default/layout: circular/g' ./1si.textile"
  system "jekyll build"
  system "cp ./_site/1en.html ./en/1en.html"
  system "cp ./_site/1si.html ./si/1si.html"
  system "sed -i 's/content-nc/content-circular/g' ./en/1en.html"
  system "sed -i 's/content-nc/content-circular/g' ./si/1si.html"
  system "wkhtmltopdf -T 15 -L 13 -R 15 ./en/1en.html datoteke/1st-Circular.pdf"
  system "wkhtmltopdf -T 15 -L 13 -R 15 ./si/1si.html datoteke/1-Obvestilo.pdf"
  system "rm 1en.textile ./en/1en.html 1si.textile ./si/1si.html"
end

namespace :post do
  desc "Create a new post"
  task :new do
    system "ruby create.rb"
  end
end
