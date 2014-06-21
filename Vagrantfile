# -*- mode: ruby -*-
# vi: set ft=ruby :
#

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define :local do |local|
    local.vm.provider "docker" do |d|
      d.build_dir = "./image"
      d.has_ssh = true
      d.vagrant_vagrantfile = "./docker_base/Vagrantfile"
    end
    local.ssh.port = 22
    local.ssh.username = "root"
    local.ssh.private_key_path = "ubuntu.key"
    #local.vm.network :forwarded_port, guest: 80, host: 8080
  end

  config.vm.define :localci do |lc|
    lc.vm.box     = "ubuntu12.04"
    lc.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-i386-vagrant-disk1.box"
  end

  config.vm.define :ci do |ci|
    ci.vm.provider :digital_ocean do |di, override|
      override.ssh.private_key_path = "~/.ssh/id_rsa"
      override.vm.box               = "digital_ocean"
      override.vm.box_url           = "https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box"
      di.client_id            = ENV["DIGITALOCEAN_CLIENT_ID"]
      di.api_key              = ENV["DIGITALOCEAN_API_KEY"]
      di.image                = "Ubuntu 14.04 x64"
      di.region               = "San Francisco 1"
      di.size                 = "512MB"
      di.ca_path              = "/usr/local/opt/curl-ca-bundle/share/ca-bundle.crt"

      if ENV['WERCKER'] == "true"
        di.ssh_key_name = "wercker"
      else
        di.ssh_key_name = "My MacBook Air"
      end
    end
  end

  # use vagrant-omnibus
  config.omnibus.chef_version = :latest
end
