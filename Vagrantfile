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
end  
