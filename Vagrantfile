Vagrant.configure("2") do |config|
    # Server 1
    config.vm.define "server-1" do |server1|
        server1.vm.box = "bento/ubuntu-22.04"
        server1.vm.network "private_network", type: "dhcp"
        server1.vm.network "private_network", ip: "192.168.56.20"

        server1.vm.provision "ansible" do |ansible|
            ansible.playbook = "provision.yml"
        end
    end

    # Server 2
    config.vm.define "server-2" do |server2|
        server2.vm.box = "bento/ubuntu-22.04"
        server2.vm.network "private_network", type: "dhcp"
        server2.vm.network "private_network", ip: "192.168.56.21"

        server2.vm.provision "ansible" do |ansible|
            ansible.playbook = "provision.yml"
        end
    end
    
    # Server 3
    config.vm.define "server-3" do |server3|
        server3.vm.box = "bento/ubuntu-22.04"
        server3.vm.network "private_network", type: "dhcp"
        server3.vm.network "private_network", ip: "192.168.56.22"

        server3.vm.provision "ansible" do |ansible|
            ansible.playbook = "provision.yml"
        end
    end

    # Target for the attack
    config.vm.define "target" do |target|
        target.vm.box = "bento/ubuntu-22.04"
        target.vm.network "private_network", type: "dhcp"
        target.vm.network "private_network", ip: "192.168.56.23"
        target.vm.network "forwarded_port", guest: 80, host: 8080
        target.vm.provision "ansible" do |ansible|
            ansible.playbook = "provision.yml"
        end
    end
end  
