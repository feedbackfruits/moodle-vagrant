# moodle-vagrant
Moodle Vagrant installer (Ubuntu 16.04, Apache, PHP7, PostgreSQL, Latest Moodle)

## Requirements:

- Vagrant (https://www.vagrantup.com/downloads.html)
- vagrant-env (https://github.com/gosuri/vagrant-env)

## Usage instructions:

- Clone moodle-vagrant: `git clone https://github.com/feedbackfruits/moodle-vagrant.git`
- Change to moodle-vagrant directory

### For VirtualBox

- Install the vagrant-vbguest plugin (https://github.com/dotless-de/vagrant-vbguest)
- Install VirtualBox (https://www.virtualbox.org/)
- Setup your .env file with the desired url for MOODLE_URL
- Execute vagrant: `vagrant up --provider=virtualbox`
- You will need to add a hosts file entry for: MOODLE_URL points to 192.168.33.10

### For Digital Ocean

- Install the vagrant-digitalocean plugin (https://github.com/devopsgroup-io/vagrant-digitalocean)
- Setup your .env file with the variables described on .env.example
- Execute vagrant: `vagrant up --provider=digital_ocean`
- You will need to add a hosts file entry for: MOODLE_URL points to just created droplet URL

## Authentication Details:

- username: admin
- password: Admin1!

This has been tested using Vagrant 1.9.1
