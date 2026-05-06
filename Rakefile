require 'dotenv'
Dotenv.load

require 'octokit'

task :default do
  client = Octokit::Client.new(:access_token => ENV.fetch("UNRAID_TEMPLATE_PAT"))
  @releases = client.releases("manyfold3d/manyfold").select{ it.published_at }

  targets = [
    "manyfold/manyfold-solo.xml"
  ]

  targets.each do |target|
    template = ERB.new(File.read("#{target}.erb"))
    output = template.result(Kernel.binding)
    File.write(target, output)
end
