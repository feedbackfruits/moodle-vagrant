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
    override.vm.box = 'digital_ocean'
    override.vm.box_url = 'https://github.com/devopsgroup-io/vagrant-digitalocean/raw/master/box/digital_ocean.box'
    provider.token = ENV['DIGITAL_OCEAN_TOKEN']
    provider.image = 'ubuntu-16-04-x64'
    provider.region = ENV['DIGITAL_OCEAN_REGION']
    provider.size = '1gb'
    provider.ssh_key_name = ENV['DIGITAL_OCEAN_SSH_KEY_NAME']
  end

  config.vm.provision 'shell' do |s|
    s.inline = 'sudo bash /vagrant/provision.sh $1'
    s.args = [ENV['MOODLE_URL']]
  end
end
