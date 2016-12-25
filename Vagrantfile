# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.provider 'virtualbox' do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = 2048
    vb.name = 'odoo_k8s'
  end
  
  VAGRANT_ROOT = File.dirname(File.expand_path(__FILE__))
  k8s_dir = File.join(VAGRANT_ROOT, 'k8s')
  etc_dir = File.join(VAGRANT_ROOT, 'config')
  # this corrects a bug in 1.8.5 where an invalid SSH key is inserted.
  if Vagrant::VERSION == "1.8.5"
    config.ssh.insert_key = false
  end
  if Vagrant.has_plugin?("vagrant-vbguest") then
     config.vbguest.auto_update = false
  end
  
  config.vm.synced_folder k8s_dir, '/home/vagrant/k8s', nfs: true, id: 'vagrant'
  config.vm.network :'private_network', ip: '195.168.50.4'
  config.vm.network 'forwarded_port', guest: 80, host: 9080  
  config.vm.network 'forwarded_port', guest: 8080, host: 8080
  config.vm.network 'forwarded_port', guest: 443, host: 8443

  # Disable SELINUX by default on each run so that k8s doesn't have issues.
  config.vm.provision :shell, run: 'always', inline: <<-SHELL
    sudo setenforce 0
  SHELL

  config.vm.provision :shell, inline: <<-SHELL
    cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=http://yum.kubernetes.io/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg
       https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF

yum install -y --no-gpgcheck docker kubelet kubeadm kubectl kubernetes-cni
systemctl enable docker && systemctl start docker
systemctl enable kubelet && systemctl start kubelet

  SHELL
end
 
