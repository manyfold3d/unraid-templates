require 'dotenv'
Dotenv.load

require 'octokit'

task :default do
  client = Octokit::Client.new(:access_token => ENV.fetch("GITHUB_ACCESS_TOKEN"))
  @releases = client.releases("manyfold3d/manyfold")

  template = ERB.new(File.read("manyfold/manyfold.xml.erb"))
  output = template.result(Kernel.binding)
  File.write("manyfold/manyfold.xml", output)
end
