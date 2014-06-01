# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
#  config.vm.box = "phusion-open-ubuntu-14.04-amd64"                                                                                                                               
#  config.vm.box_url = 
#    "https://oss-binaries.phusionpassenger.com/vagrant/boxes/latest/ubuntu-14.04-amd64-vbox.box"

  config.vm.provider "docker" do |d|
    d.build_dir = "./image"
    d.has_ssh = true
    d.vagrant_vagrantfile = "./docker_base/Vagrantfile"
  end

  config.ssh.port = 22
  config.ssh.username = "root"
  config.ssh.private_key_path = "ubuntu.key"
  # config.vm.network :forwarded_port, guest: 80, host: 8080

#  config.vm.provider "virtualbox" do |vb|
    # Use VBoxManage to customize the VM. For example to change memory:
#    vb.customize ["modifyvm", :id, "--memory", "2048"]
#   vb.vm.synced_folder "../", "/"
#  end

#  config.vm.provision :shell, inline: <<-EOF
#    echo "Hello world"
#  EOF

  config.vm.define "web" do |c|
#    c.vm.provision :shell do |shell|
#    shell.path = "provision.sh"
#    shell.args = "app"
#    end
  end

  config.vm.define "db" do |c|
#    c.vm.provision :shell do |shell|
#    shell.path = "provision.sh"
#    shell.args = "app"                                                                                                                                                                 
#    end
  end

end
