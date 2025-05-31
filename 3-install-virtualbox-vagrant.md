# using virtualbox as the virtualization provier

```bash
sudo apt update && sudo apt upgrade -y
```

install virtualbox and vagrant

```bash
# virtualbox
sudo apt install -y virtualbox

# vagrant
wget https://releases.hashicorp.com/vagrant/2.4.1/vagrant_2.4.1-1_amd64.deb
sudo dpkg -i vagrant_2.4.1-1_amd64.deb
sudo apt-get install -f
vagrant --version
```

# using the kode kloud cka repo

First I forked the repo and then need to clone it down to my server

```
# install openssh client
sudo apt install openssh-client
# create ssh keys on server
ssh-kegen -r rsa
cat ~/.ssh/id_rsa.pub -> copy to github
# install git :)
sudo apt install git -y
# clone forked repo to my baremetal server
git clone git@github.com:gramOB/certified-kubernetes-administrator-course.git
```

Then go to the virtualbox subdirectory and run vagrant status to confirm what is about to be built

```bash
gob@gob-X10SLM-F:~/certified-kubernetes-administrator-course/kubeadm-clusters/virtualbox$ vagrant status
==> vagrant: A new version of Vagrant is available: 2.4.6 (installed version: 2.4.1)!
==> vagrant: To upgrade visit: https://www.vagrantup.com/downloads.html

Current machine states:

controlplane              not created (virtualbox)
node01                    not created (virtualbox)
node02                    not created (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.

```

Then run vagrant up and vagrant status

```bash
vagrant up
---
VM build complete!

Use either of the following to access any NodePort services you create from your browser
replacing "port_number" with the number of your NodePort.

  http://192.168.2.73:port_number
  http://192.168.2.72:port_number

---
gob@gob-X10SLM-F:~/certified-kubernetes-administrator-course/kubeadm-clusters/virtualbox$ vagrant status
Current machine states:

controlplane              running (virtualbox)
node01                    running (virtualbox)
node02                    running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.

```


Access the vms from the host with vagrant ssh `<hostname>`

```
vagrant ssh controlplane
```
