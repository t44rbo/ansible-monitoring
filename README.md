# Ansible monitoring

## What it does
- Configures new server for monitoring-stack deployment

## Roles
- Docker
  - Install dependencies
  - Add GPG key docker
  - Add docker repo
  - Install docker
  - Add user to docker group

- Monitoring
  - Copy deploy key
  - Add GitHub to ssh config
  - Add GitHub key to known_hosts
  - Clone or update repository
  - Add .env file
  - Start monitoring-stack

## Requirements

- Ansible installed on control node
- SSH access to target hosts
- Create roles/monitoring/defaults/main.yml from example
- Add deploy key to /roles/monitoring/files/

## Usage
```bash
git clone https://github.com/t44rbo/ansible-monitoring.git
cp roles/monitoring/defaults/main.yml.example roles/monitoring/defaults/main.yml
nano roles/monitoring/defaults/main.yml # fill in secrets
nano inventory/hosts.ini # set your hosts and their username
ansible-playbook -i inventory/hosts.ini site.yml 
```
## Project structure
```
ansible-monitoring/
|-- README.md
|-- inventory
|   `-- hosts.ini
|-- roles
|   |-- docker
|   |   |-- defaults
|   |   |-- handlers
|   |   `-- tasks
|   |       `-- main.yml
|   `-- monitoring
|       |-- defaults
|       |   `-- main.yml.example
|       |-- files # here should be deploy key
|       `-- tasks
|           `-- main.yml
`-- site.yml
```
