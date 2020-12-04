# Web3Signer Vagrant Environment

This repository provide a quick way to start [Web3Signer](https://github.com/ConsenSys/web3signer) in a local 
VirtualBox VM using Vagrant. This is useful during the development of the Web3Signer ansible-role which allows quickly
perform a deployment in a local isolated environment.


## Pre-Requisites 
- [Vagrant](https://www.vagrantup.com/)
- [VirtualBox](https://www.virtualbox.org/)
- Python3


## Installation

Create a virtual env for w3s and install required packages.
```bash
# Create  venv
python3 -m venv ~/.w3s
source ~/.w3s/bin/activate

# Install requirements
pip install -r requirements.txt
```

Install ansible roles
```bash
ansible-galaxy install -r requirements.yml
```

Now run `vagrant up` command and it will deploy VM and install Java, Postgres and Web3Signer. Ssh into VM with command
`vagrant ssh web3signer`


## Start / Stop 

Application run as systemd service and command `systemctl start/stop/status web3signer` can be used to 
manage the Web3Signer service.

## Configuration

### Web3Signer
Installation can be customized using the file `vars/web3signer.yml` file. Default vars setup a basic web3signer 
application. Parameters for database creation and Web3Signer are linked via this file.

### Signing Keys
Example key(unencrypted) is available at `vars/key1.yml`. Add any keys here. Remember never check-in production keys
or parameters to a git repository unless those are encrypted. 

