# Ansible for Traefik & Dokku 

We need to provide some servers with many tools, like frontend + backend, and other apps. 
And we want to serve all services thanks to a reverse-proxy.

For that, I propose this playbook. It installs [Dokku](https://dokku.com/), it's a small PaaS to deploy many apps like Heroku but it allows us to have other tools and run a docker-compose or anything else. 
 
 
## How it works 


## Why change Dokku default nginx config ? 

Traefik needs to listen on port :80 to serve on other intern services.
And if Dokku use also port 80, Traefik can’t work. 
To solve that, I decided to change nginx Dokku config for it to listen in localhost:1000

## Getting Started 

1. Clone the repo : 

```shell
git clone 
```

2. Install Role : 

```shell
ansible-galaxy install dokku_bot.ansible_dokku
```

3. Copy vars :

```shell
cp vars/sample.app-env.yaml vars/app-env.yaml
```

4. Fill vars : 
- `SSH_KEY_PUB` for your personal ssh key pub `etc/.ssh/_.pub`.
- `SSH_KEY_NAME` name associated to your key, it creates Dokku user with this name. 

3. Run Ansible provision : 

```shell
ansible-playbook playbook.yaml
```

4. Access 

## How to use ? 
If you want use Dokku to deploy your app you simply need to connect to your server with ssh : create app and deploy 

## How to use with Vagrant 

1. Simply run : 
```shell
vagrant up --provision
```
