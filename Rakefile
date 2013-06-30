desc "compile and run the site"
task :sass do
  pids = [
    spawn("jekyll"),
    spawn("scss --watch assets:css")
  ]

  trap "INT" do
    Process.kill "INT", *pids
    exit 1
  end

  loop do
    sleep 1
  end
end

desc "deploy to GitHub"
task :deploy do
  puts "## Deploying to Github Pages.."
  system "git push origin master --force"
  puts "## Deploy Complete!"
end
