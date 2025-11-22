# Installation de Docker 

### Supprimer les anciennes version de docker (Optionnel)

```
sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-doc podman-docker containerd runc | cut -f1)
```

### Configuration des dépots

```
# Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/debian
Suites: $(. /etc/os-release && echo "$VERSION_CODENAME")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update
```

### Installation des packets

```
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
---

## Verifier l'état du service docker
`
sudo systemctl status docker
`
## Démarrer le service Docker
`
sudo systemctl start docker 
`
## Arreter le service 
`
Sudo systemctl stop docker
`
## Vérifier que Docker est OK 

```
sudo docker run hello-world
```
---
Voici un **README.md clair et concis** regroupant les **commandes Docker les plus utilisées et essentielles**.

---

# Docker – Commandes essentielles

Ce document regroupe les commandes Docker les plus utiles pour gérer les images, conteneurs, volumes et réseaux. Elles couvrent l’essentiel des opérations quotidiennes pour manipuler Docker efficacement.

---

## 📦 Images

### Télécharger une image

```bash
docker pull <image>
```

### Lister les images disponibles

```bash
docker images
```

### Supprimer une image

```bash
docker rmi <image>
```

### Construire une image depuis un Dockerfile

```bash
docker build -t <nom:image> .
```

---

## 🐳 Conteneurs

### Lister les conteneurs

```bash
docker ps           # conteneurs en cours d’exécution
docker ps -a        # tous les conteneurs
```

### Créer et lancer un conteneur

```bash
docker run <image>
```

### Démarrer un conteneur en tâche de fond (detach)

```bash
docker run -d <image>
```

### Définir un nom de conteneur

```bash
docker run --name mon_conteneur <image>
```

### Monter un port

```bash
docker run -p <port_local>:<port_conteneur> <image>
```

### Monter un volume

```bash
docker run -v <chemin_hote>:<chemin_conteneur> <image>
```

### Accéder au shell d’un conteneur

```bash
docker exec -it <conteneur> bash
```

---

## 🔄 Gestion des conteneurs

### Démarrer / arrêter un conteneur

```bash
docker start <conteneur>
docker stop <conteneur>
```

### Supprimer un conteneur

```bash
docker rm <conteneur>
```

### Supprimer tous les conteneurs arrêtés

```bash
docker container prune
```

---

## 📁 Volumes

### Lister les volumes

```bash
docker volume ls
```

### Supprimer un volume

```bash
docker volume rm <volume>
```

### Supprimer les volumes non utilisés

```bash
docker volume prune
```

---

## 🌐 Réseaux

### Lister les réseaux

```bash
docker network ls
```

### Créer un réseau

```bash
docker network create <nom>
```

### Supprimer un réseau

```bash
docker network rm <nom>
```

---

## 🧹 Nettoyage global

### Supprimer tout ce qui n'est pas utilisé

```bash
docker system prune
```

### Supprimer absolument tout (dangereux)

```bash
docker system prune -a --volumes
```

---

## 📄 Logs et inspection

### Voir les logs

```bash
docker logs <conteneur>
```

### Inspecter un conteneur ou une image

```bash
docker inspect <conteneur|image>
```

---

## ⚙️ Docker Compose

### Lancer un stack

```bash
docker-compose up
```

### Lancer en arrière-plan

```bash
docker-compose up -d
```

### Arrêter les services

```bash
docker-compose down
```

### Rebuild sans cache

```bash
docker-compose build --no-cache
```

---

Si tu veux, je peux aussi :

* créer une **version avancée** du README
* ajouter des **exemples pratiques**
* faire un **mémo Docker + Docker Compose**
* générer un **poster / cheat sheet PDF**

Tu veux un de ces ajouts ?
