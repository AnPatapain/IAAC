# automated_pentest
## Run Vagrantfile to start 3 virtual machines (2 Servers and 1 Target)
**Check the vagrantfile**:  
```nano Vagrantfile```  
Check ip address of your local machine: ```ip a``` for me it's 192.168.56.1  
Replace the ip address of three Vms. 3 Vms must be in the same network interface of your local machine, for me the interface is: 192.168.56.*  
```
# Replace the ips that match your network interface
server1.vm.network "private_network", ip: "192.168.56.20"    
server2.vm.network "private_network", ip: "192.168.56.21"  
target.vm.network "private_network", ip: "192.168.56.22"  
```

**Startup 3 Vms**:  
```vagrant up```    


**Start ddos task with Ansible**  
The inventory is the file that defines all remote servers that ansible manages. To see the file  
```cat .vagrant/provisioners/ansible/inventory/```  

_ddos.yml_ is the playbook that makes server1 and server2 do the DDOS task concurently. To run it  
```ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory ddos.yml```  

**Monitor the result**  
Go to the target:  
```
vagrant ssh target
ip a
sudo tcpdump -i <your interface>
```    
Turn on your terminal then try to fetch default apache2 page from the target:  
```curl <ip of target>```

 
