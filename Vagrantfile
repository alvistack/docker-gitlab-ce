Vagrant.configure("2") do |config|
  config.vm.provider :docker do |docker, override|
    docker.image = "alvistack/gitlab-ce-17.3"
    docker.pull = true

    override.vm.synced_folder "./", "/vagrant"
  end
end
