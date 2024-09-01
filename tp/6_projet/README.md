# Registry harbord
Dans cette configuration Vagrant,vous allez pouvoir déployer une VM dans laquelle on aura préinstallé un moteur Docker.
```bash 
git clone https://github.com/RousselTM/docker-formation.git
cd docker-formation/TP/4_docker_swarm
vagrant up
```
Contrairement aux précédents TP, cette configuration va déployer 3 VMs. Vous pouvez vérifier le statut avec la commande :
```bash 
vagrant status
```
Il suffit de saisir cette commande pour vous connecter à une des machines : 
```bash 
vagrant ssh <NOM_VM>
```
Il faudra passer en root
```bash 
sudo su - root
```
Puis lancer l'initialisation de Docker Swarm depuis la machine manager
```bash 
docker swarm init --advertise-addr ${manager_ip}
```
Pour récupérer le token pour faire le join 
```bash 
docker swarm join-token -q worker
```
Si vous souhaitez initialiser automatiquement Swarm à l'installation de la machine vous pouvez lancer cette commande 
```bash 
export DEPLOY_SWARM=true; vagrant up
```