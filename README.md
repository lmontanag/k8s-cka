# Install K8S cluster using vagrant and ansible

based on [Kubernetes Setup Using Ansible and Vagrant](https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/)

Install vagrant & vagrant-vbguest plugin

```bash
brew install vagrant
vagrant plugin install vagrant-vbguest
```

Install ansible on a virtual environment

```bash
# create a python virtual environment
python3 -m venv ~/.venv-ansible
# activate environment
source ~/.venv-ansible/bin/activate
# install ansible
pip install ansible
# deactivate environment
deactivate
```

Starts and provisions the vagrant environment

```bash
# activate environment
source ~/.venv-ansible/bin/activate
vagrant up
```

Access to the servers

```bash
## Accessing master
vagrant ssh k8s-master
vagrant@k8s-master:~$ kubectl get nodes
NAME         STATUS   ROLES                  AGE   VERSION
k8s-master   Ready    control-plane,master   20h   v1.21.5
node-1       Ready    <none>                 19h   v1.21.5
node-2       Ready    <none>                 19h   v1.21.5


## Accessing nodes
vagrant ssh node-1
vagrant ssh node-2
```

additional vagrant commands

```bash
resume          resume a suspended vagrant machine
suspend         suspends the machine
status          outputs status of the vagrant machine
```

## useful links

- [Training and Certification](https://docs.linuxfoundation.org/tc-docs/)
- [Important Instructions: CKA and CKAD](https://docs.linuxfoundation.org/tc-docs/certification/tips-cka-and-ckad)
  - The CKA & CKAD environments are currently running Kubernetes v1.21.
- [Platform Selection](https://docs.linuxfoundation.org/tc-docs/certification/lf-candidate-handbook/exam-preparation-checklist#platform-selection-1)
  - for CKA the Platform Option Available is `Ubuntu 18.04`
- [calico requirements](https://docs.projectcalico.org/archive/v3.20/getting-started/kubernetes/requirements)

## Configuring a cgroup driver

Both the container runtime and the kubelet have a property called "[cgroup driver](https://kubernetes.io/docs/setup/production-environment/container-runtimes/)", which is important for the management of cgroups on Linux machines.

Warning:
Matching the container runtime and kubelet cgroup drivers is required or otherwise the kubelet process will fail.

See [Configuring a cgroup](https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/configure-cgroup-driver/) driver for more details.

here the info to setup a cgroup driver for [docker](https://kubernetes.io/docs/setup/production-environment/container-runtimes/#docker)

## Troubleshooting

- [Running Ansible Manually](https://docs.ansible.com/ansible/2.4/guide_vagrant.html#running-ansible-manually)

  ```bash
  # run master-playbook.yml
  ansible-playbook --private-key=~/.vagrant.d/insecure_private_key --extra-vars "node_ip=192.168.50.10" -u vagrant -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory kubernetes-setup/master-playbook.yml
  # run unly join-command
  ansible-playbook --private-key=~/.vagrant.d/insecure_private_key --extra-vars "node_ip=192.168.50.10" -u vagrant -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory kubernetes-setup/master-playbook.yml --tags "join-command"
  ```

- troubleshoot kubelet

  ```bash
  If you are on a systemd-powered system, you can try to troubleshoot the error with the following commands:
  - 'systemctl status kubelet'
  - 'journalctl -xeu kubelet'
  ```

- [Troubleshooting kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/troubleshooting-kubeadm/)
