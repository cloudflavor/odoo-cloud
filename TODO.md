* Install vbguest plugin `vagrant plugin install vagrant-vbguest` (on fedora this requires ruby header files from the `ruby-devel` package to be installed)
* Setenforce to 0.  
* Install EPEL.  
* yum install kernel-devel kernel-headers dkms yum groupinstall "Development Tools"
* Add virtualbox guest additions for centos to be able to fw ports to the host without problems.  
* [Use the online calico plugin.]( http://docs.projectcalico.org/v2.0/getting-started/kubernetes/installation/hosted/kubeadm/calico.yaml)
* Add kubernetes repository and install `docker` `kubelet` `kubeadm` `kubectl` `kubernetes-cni`.
* Follow instructions to setup an all-in-one kubernetes cluster with [`kubeadm init`](http://kubernetes.io/docs/getting-started-guides/kubeadm/).
* Bootstrap kubernetes deployment config for Odoo with a postgresql backing service.   
* Create vagrant box for easy demo.  
* Update [README.md](README.md) with instructions on how to run the application.  
* Screen record application demo with ASCII Cinema.  
* Profit.  
* Do a little dance.  

##### For the future
* Automate above steps with Ansible.  
* Update [Provisioning.md](Provisioning.md) with the right instructions for self-provisioning the demo.  
