vagrant-docker
==============
vagrant-docker

[![wercker status](https://app.wercker.com/status/ff4e041d6ab2c20e1a0879e89fcb6891/m "wercker status")](https://app.wercker.com/project/bykey/ff4e041d6ab2c20e1a0879e89fcb6891)

[![Build Status](https://travis-ci.org/koudaiii/vagrant-docker.svg?branch=master)](https://travis-ci.org/koudaiii/vagrant-docker)

### Installation

Install vagrant and virtualbox
Sign up digital_ocean

[vagrant](http://www.vagrantup.com/)

[virtualbox](https://www.virtualbox.org/)

[digital_ocean](https://www.digitalocean.com/)

### Usege

      $ vagrant plugin install vagrant-omnibus
      $ vagrant plugin install vagrant-digitalocean
      $ brew install curl-ca-bundle

[vagrant-omunibus](https://github.com/schisamo/vagrant-omnibus)

[vagrant-digitalocean](https://github.com/smdahlen/vagrant-digitalocean)

### Run

#### local

      $ vagrant up --provider=docker local
      $ vagrant up --provider=digital_ocean ci

#### digital_ocean

      $ mv .digital_ocean.example .digital_ocean
      $ vi .digital_ocean
      # set Client_ID and set API_KEY
      $ souce .digital_ocean
