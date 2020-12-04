Vagrant.configure("2") do |config|
  config.vm.box_check_update = false
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.memory = 4096
    v.cpus = 2
  end

  %w{web3signer}.each_with_index do |name, i|
    config.vm.define name do |server|
      server.vm.box = "ubuntu/focal64"
      server.vm.hostname = name
      server.vm.network :private_network, ip: "172.24.20.#{i + 31}"

       server.vm.provision "ansible" do |ansible|
         ansible.playbook = "playbook-web3signer.yml"
       end
    end
  end

end
