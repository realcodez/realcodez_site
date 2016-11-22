def dest_dir
  File.expand_path('../realcodez.github.io', __dir__)
end

task :build do
  sh "bundle exec jekyll build --source site --destination #{dest_dir}"
end

task :serve do
  sh "bundle exec jekyll serve -s site -d #{dest_dir} -w"
end
