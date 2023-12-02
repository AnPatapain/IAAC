Vagrant.configure("2") do |config|
    nodes = [
        { name:  "manager-node", ip: "192.168.56.20"},
        { name:  "worker-node-1", ip: "192.168.56.21"},
        { name:  "worker-node-2", ip: "192.168.56.22"},
        { name:  "worker-node-3", ip: "192.168.56.23"}
    ]

    nodes.each do |node| 
        config.vm.define node[:name] do |n|
            n.vm.box = "bento/ubuntu-22.04"
            n.vm.provision :docker

            # Change ssh from key based connection to password based connection
            n.vm.provision "shell", inline: <<-SHELL
                sudo sed -i 's/^\\s*PasswordAuthentication\\s\\+no/PasswordAuthentication yes/' /etc/ssh/sshd_config
                sudo systemctl restart sshd.service
            SHELL

            n.vm.network "private_network", ip: node[:ip]
            n.vm.hostname = node[:name]
        end
    end
end  
