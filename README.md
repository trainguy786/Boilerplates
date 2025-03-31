# Boilerplates
## A set of example templates and configurations, such as Docker Compose and K8s manifests.

This Repo is for those who want to deploy docker / Kubernetes services quickly with only minimal editing required. These are a collection of projects I've either deployed or played around within my homelab. They are simply **templates**. Feel free to use these manifests for your own use. 
### How to use on your machine:
#### Docker:
1) Install Docker & Docker compose from https://docs.docker.com/engine/install/ubuntu/ .
2) Clone this repo (in your home folder).
```bash
git clone https://github.com/trainguy786/Boilerplates.git
```
3) switch to the git directory and to a project you want to deploy (eg: filebrowser).
```bash
cd Boilerplates/docker-compose/filebrowser
```
4) Edit the docker compose file to suit your needs. 
5) Deploy with the command (if not root):
```bash
sudo docker compose up -d
```
#### Kubernetes:
1) Install K3s and the required components. I recommend this Repo https://github.com/techno-tim/k3s-ansible .
2) Install helm https://helm.sh/docs/intro/install/ .
3) Clone this repo (in your home folder).
```bash
git clone https://github.com/trainguy786/Boilerplates.git
```
3) switch to the git directory and to Kubernetes (eg: Lets say you want to deploy Portainer).
```bash
cd Boilerplates/kubernetes
```
4) Edit the Kubernetes manifest to suit your needs.
5) Deploy with the command:
```bash
kubectl apply -f ./portainer/ -n portainer
```
> [!note]
> Make sure you create the namespace before deploying it. 
```
kubetcl create namepace portainer
```
### Further info
- `domain.local` needs to be replaced with your domain
- Make sure you edit the volume mounts and their **permissions**!
- I'm currently using a specific k3s version: 1.30.2.k3s2. So I'm not sure if these Kubernetes manifests will work for future versions.
- You may notice ingresses aren't included in most of the manifests. I currently don't use traefik ingresses and instead rely on another instance of Traefik running on docker by pointing to the service's loadbalancer IP.
----
### Known Issues
- [ ] Some Kubernetes manifests are out of date. EG: portainer is always changing
### How to tweak this project for your own use
You can do whatever you want. Fork it or clone it for your own personal use.
