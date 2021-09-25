# Install K8S cluster using vagrant and ansible

based on [Kubernetes Setup Using Ansible and Vagrant](https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/)

Install vagrant

```bash
brew install vagrant
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
