Vagrant.configure("2") do |config|
  if Vagrant.has_plugin?("vagrant-vbguest")
    config.vm.provider :virtualbox do |vb|
      config.vbguest.auto_update = false
    end
  end

  config.vm.box = "ubuntu/focal64"

  config.vm.network "public_network", bridge: "en0: Wi-Fi (Wireless)", ip: "192.168.2.10"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 1
  end

  config.vm.define "dokku" do |machine|
    machine.vm.provision "ansible" do |ansible|
      ansible.verbose = true
      ansible.playbook = 'playbook.yaml'
    end
  end

end