# network bridge
**Private Network Bridge**: A private network bridge is like a virtual router. It assigns itself a private IP address and creates a DHCP server. The KVM virtual machines that are connected to this network bridge get IP addresses via the DHCP server of the bridge. The network bridge uses NAT (Network Address Translation) to provide internet connectivity to the KVM virtual machines. The KVM virtual machines that are connected to the private network bridge can communicate between themselves. The KVM host (where the virtual machines are running) can directly access the virtual machines as well. But the virtual machines are not accessible from the outside network.

**Public Network Bridge**: A public network bridge is like a virtual switch. You can connect one physical network interface to the bridge, and the KVM virtual machines that use the network bridge will assign themselves IP addresses using the DHCP server running on the router on which the physical network interface is connected to. If a public network bridge is used, the KVM virtual machines connected to it will get IP addresses from your physical router or network devices. The KVM virtual machines will be accessible from each other, the KVM host as well as the outside network.


- document
```bash
virsh list --all  #  view the list of available VMs
systemctl start libvirtd  
virsh console simisec # connect a virtual machine
```