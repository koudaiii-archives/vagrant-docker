# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "app" do |app|
    app.vm.provider "docker" do |d|
      d.build_dir = "./image"
      d.has_ssh = true
    end
    app.ssh.port = 22
    app.ssh.username = "root"
    app.ssh.private_key_path = "ubuntu.key"
  end

end
