# single node cluster installation
## make sure the node user can run docker 
```
sudo usermod -aG docker ubuntu
```
```
# verify it by run this command from your workstation
ubuntu@rke-workstation:~$ ssh ubuntu@10.88.1.x docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
```
ubuntu@rke-workstation:~$ rke config
[+] Cluster Level SSH Private Key Path [~/.ssh/id_rsa]: 
[+] Number of Hosts [1]: 
[+] SSH Address of host (1) [none]: 10.88.1.108
[+] SSH Port of host (1) [22]: 
[+] SSH Private Key Path of host (10.88.1.108) [none]: 
[-] You have entered empty SSH key path, trying fetch from SSH key parameter
[+] SSH Private Key of host (10.88.1.108) [none]: 
[-] You have entered empty SSH key, defaulting to cluster level SSH key: ~/.ssh/id_rsa
[+] SSH User of host (10.88.1.108) [ubuntu]: 
[+] Is host (10.88.1.108) a Control Plane host (y/n)? [y]: 
[+] Is host (10.88.1.108) a Worker host (y/n)? [n]: y
[+] Is host (10.88.1.108) an etcd host (y/n)? [n]: y
[+] Override Hostname of host (10.88.1.108) [none]: 
[+] Internal IP of host (10.88.1.108) [none]: 
[+] Docker socket path on host (10.88.1.108) [/var/run/docker.sock]: 
[+] Network Plugin Type (flannel, calico, weave, canal, aci) [canal]: 
[+] Authentication Strategy [x509]: 
[+] Authorization Mode (rbac, none) [rbac]: 
[+] Kubernetes Docker image [rancher/hyperkube:v1.21.8-rancher2]: 
[+] Cluster domain [cluster.local]: 
[+] Service Cluster IP Range [10.43.0.0/16]: 
[+] Enable PodSecurityPolicy [n]: 
[+] Cluster Network CIDR [10.42.0.0/16]: 
[+] Cluster DNS Service IP [10.43.0.10]: 
[+] Add addon manifest URLs or YAML files [no]: 
```

```
ubuntu@rke-workstation:~$ rke up
INFO[0000] Running RKE version: v1.3.6                  
INFO[0000] Initiating Kubernetes cluster                
INFO[0000] [dialer] Setup tunnel for host [3.104.124.16] 
''''''
INFO[0199] [ingress] ingress controller nginx deployed successfully 
INFO[0199] [addons] Setting up user addons              
INFO[0199] [addons] no user addons defined              
INFO[0199] Finished building Kubernetes cluster successfully 
```

```
ubuntu@rke-workstation:~$ mkdir .kube
ubuntu@rke-workstation:~$ cp kube_config_cluster.yml /$HOME/.kube/config
ubuntu@rke-workstation:~$ chmod 700 /home/ubuntu/.kube/config
ubuntu@rke-workstation:~$ kubectl get node
NAME           STATUS   ROLES                      AGE   VERSION
3.104.124.16   Ready    controlplane,etcd,worker   47m   v1.21.8
```