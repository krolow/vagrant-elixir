def install_dep(name, params = nil)
  "(mkdir -p /etc/puppet/modules && puppet module --modulepath /etc/puppet/modules list | grep #{name}) || puppet module install #{name} #{params}"
end

Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.network :private_network, ip: "192.168.56.244"
  config.ssh.forward_agent = true

  config.vm.provision :shell do |shell|
    shell.inline = install_dep("garethr-elixir")
  end

  config.vm.provision "puppet" do |puppet|
    puppet.manifests_path = "manifests"
    puppet.options = ['--verbose']
  end
end
