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

## useful links

- [Training and Certification](https://docs.linuxfoundation.org/tc-docs/)
- [Important Instructions: CKA and CKAD](https://docs.linuxfoundation.org/tc-docs/certification/tips-cka-and-ckad)
- [Platform Selection](https://docs.linuxfoundation.org/tc-docs/certification/lf-candidate-handbook/exam-preparation-checklist#platform-selection-1)
  - for CKA the Platform Option Available is `Ubuntu 18.04`

## Troubleshooting

- [Running Ansible Manually](https://docs.ansible.com/ansible/2.4/guide_vagrant.html#running-ansible-manually)
