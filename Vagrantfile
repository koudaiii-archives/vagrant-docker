# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.provider "docker" do |d|
    d.build_dir = "./image"
    d.has_ssh = true
    d.vagrant_vagrantfile = "./docker_base/Vagrantfile"
  end

  config.ssh.port = 22
  config.ssh.username = "root"
  config.ssh.private_key_path = "ubuntu.key"
  #config.vm.network :forwarded_port, guest: 80, host: 8080

end
