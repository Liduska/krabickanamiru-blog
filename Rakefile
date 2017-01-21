require "rubygems"
require "tmpdir"

namespace :site do

  desc "Generate and publish blog to gh-pages"
  task :publish do
    Dir.mktmpdir do |tmp|
      cp_r "_site/.", tmp
      Dir.chdir tmp
      rm "key"
      system "git init"
      system "git add ."
      system "git config user.name \"Travis-CI\""
      system "git config user.email \"travis@krabickanamiru.cz\""
      message = "Site updated at #{Time.now.utc}"
      system "git commit -m #{message.inspect}"
      system "git push --force --quiet \"git@github.com:Liduska/krabickanamiru-blog.git\" master:gh-pages"
    end
  end
end
