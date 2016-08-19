Vagrant.configure('2') do |config|

  config.vm.box = 'bstopp/centos-7.1-nocm-aem'

  config.vm.graceful_halt_timeout = 300
  config.vm.base_mac = '0800277C11F2'
  config.vm.host_name = 'vagrant.aem'

  config.vm.provider 'virtualbox' do |v|
    v.name = 'dev-aem'
    v.cpus = 2
    v.memory = 5120
  end

  config.vm.provision :shell, path: 'setup/update-vm.sh'
  config.vm.provision :shell, path: 'setup/update-puppet.sh'
  config.vm.provision :puppet do |puppet|
    puppet.environment = 'local'
    puppet.environment_path = 'puppet/environments'
    puppet.module_path = 'puppet/modules'
  end

  config.vm.network :forwarded_port, guest:80, host:10080
  config.vm.network :forwarded_port, guest:8080, host:18080
  config.vm.network :forwarded_port, guest:8009, host:18009
  config.vm.network :forwarded_port, guest:4502, host:4502
  config.vm.network :forwarded_port, guest:4503, host:4503
  config.vm.network :forwarded_port, guest:30300, host:30300
  config.vm.network :forwarded_port, guest:30303, host:30303
  config.vm.network :forwarded_port, guest:30304, host:30304

end
