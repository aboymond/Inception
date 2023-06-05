
    ##### 1) Comprendre les exigences : Lisez attentivement les spécifications du projet pour comprendre les services requis, les contraintes de construction des images Docker, les règles de réseau, les volumes nécessaires et les bonnes pratiques.

    ##### 2) Apprendre Docker et Docker Compose : Si vous n'êtes pas familier avec Docker et Docker Compose, familiarisez-vous avec ces technologies. Vous pouvez consulter la documentation officielle de Docker et Docker Compose pour apprendre les concepts de base, les commandes et les bonnes pratiques.

    ##### 3) Installer une machine virtuelle : Configurez une machine virtuelle sur laquelle vous effectuerez le projet. Vous pouvez utiliser des solutions comme VirtualBox ou VMware pour créer une machine virtuelle compatible avec votre système d'exploitation.

    4) Préparer l'environnement de développement : Configurez votre machine virtuelle avec le système d'exploitation choisi (Alpine Linux ou Debian Buster). Installez Docker et Docker Compose dans votre machine virtuelle en suivant les instructions officielles.

    5) Créer les Dockerfiles : Pour chaque service requis (NGINX, WordPress + php-fpm, MariaDB), créez un Dockerfile correspondant en utilisant le système d'exploitation choisi. Respectez les bonnes pratiques d'écriture de Dockerfiles et assurez-vous de ne pas inclure de mots de passe dans ces fichiers. Utilisez les variables d'environnement pour la configuration.

    6) Configurer le docker-compose.yml : Créez un fichier docker-compose.yml pour décrire l'ensemble de votre infrastructure. Définissez les services nécessaires (NGINX, WordPress, MariaDB), spécifiez les liens entre les services, configurez les volumes et définissez le réseau Docker nécessaire. Assurez-vous de configurer le redémarrage automatique des containers en cas de crash.

    7) Gérer les volumes : Créez les volumes nécessaires pour stocker la base de données WordPress et les fichiers du site WordPress. Assurez-vous de spécifier le chemin du volume sur la machine hôte, conformément aux spécifications du projet.

    8) Configurer le réseau : Configurez le docker-network pour connecter les containers entre eux. Évitez d'utiliser des options telles que network: host, --link ou links:, car elles sont interdites. Assurez-vous que votre container NGINX est le seul point d'entrée de l'infrastructure via le port 443 en utilisant le protocole TLSv1.2 ou TLSv1.3.

    9) Gérer les utilisateurs : Configurez la base de données MariaDB avec les deux utilisateurs requis, dont l'un sera le compte Admin pour WordPress. Assurez-vous que l'username de l'Admin ne contient pas les mots "admin" ou "Admin", comme spécifié.

    10) Assurer la sécurité : Configurez votre nom de domaine pour pointer vers votre adresse IP locale. Utilisez votre login pour le nom de domaine, par exemple, login.42.fr. Configurez le protocole TLSv1.2 ou TLSv1.3 pour le container NGINX afin de garantir la sécurité des communications.

    11) Gestion des variables d'environnement : Utilisez les variables d'environnement pour configurer vos services Docker. Il est recommandé de créer un fichier .env à la racine du dossier srcs pour stocker vos variables d'environnement.

    12) Construction et déploiement : Utilisez votre Makefile pour appeler les Dockerfiles et construire les images Docker nécessaires. Assurez-vous de ne pas utiliser des images pré-construites provenant de DockerHub, car cela est interdit pour Alpine et Debian. Assurez-vous que vos containers se lancent correctement sans recourir à des "hacky patches" ou des boucles infinies.

### Sources:

#### DOCKER COMPOSE:
https://www.youtube.com/watch?v=pMAGe6nTkws&t=480s

#### NGINX:
https://www.youtube.com/watch?v=YD_exb9aPZU

#### PHP FPM:
https://www.youtube.com/watch?v=4K0nbiFLDHg&t=212s

