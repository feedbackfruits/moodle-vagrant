Vagrant.configure(2) do |config|
  config.env.enable
  config.vm.hostname = 'Moodle'
  config.vm.box = 'ubuntu/xenial64'
  config.vm.network 'private_network', ip: '192.168.33.10'
  config.vm.synced_folder '.', '/vagrant', create: true
  config.vm.synced_folder './moodle/', '/var/www/moodle', create: true, owner: 'www-data', group: 'www-data'

  config.vm.provider :virtualbox do |vb|
    vb.name = 'moodle'
    vb.memory = 1024
    vb.cpus = 2
  end

  config.vm.provider :digital_ocean do |provider, override|
    override.ssh.private_key_path = '~/.ssh/id_rsa'
    provider.token = ENV['DIGITAL_OCEAN_TOKEN']
    provider.image = 'ubuntu-16-04-x64'
    provider.region = 'ams2'
    provider.size = '1gb'
    provider.ssh_key_name = ENV['DIGITAL_OCEAN_SSH_KEY']
  end

  config.vm.provision 'shell', inline: <<-SHELL
		sudo bash /vagrant/provision.sh
	SHELL
end
