# Networking 

- In a node setup, the Pods host containers.
- Each Pod is assigned an IP address in the order of 10.24.x.x.
- In each Node, Kubernetes creates an internal IP address (10.24.0.0) to which all Pods attach.
- This default network also assigns IP addresses to all Pods created within the node.
- If two nodes running Kubernetes have been assigned the IP addresses 192.168.1.2 and 192.168.1.3, there is no automatic network 
   connection between Pods in these nodes.

# To establish communication between Pods in different nodes, two conditions should be met:

- All containers and Pods can automatically communicate with each other without needing a Network Address Translator (NAT).
Nodes and containers can communicate back and forth without requiring a NAT.


![image](https://github.com/Bhavana851/Kubernetes-Practice/assets/153347669/696f08d3-dd30-46ab-aeb5-4f5b227320d9)

- will then use a custom networking solution (e.g., Cisco, Cilium, Flannel, VMware NSX, etc.) to manage networking within a node and assign addresses to virtual networks within the node.
-  These solutions also create virtual networks within the node and establish communication between nodes using routing algorithms.






