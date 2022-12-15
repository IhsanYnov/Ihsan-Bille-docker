Début du TP 
a. Récupérer l’image sur le Docker Hub :

   > docker pull nginx
   
b. Vérifier que cette image est présente en local :

   > docker images 
   
c. Créer un fichier index.html simple

   > mkdir test
   > cd test
   > nano index.html
   
d. Démarrer un conteneur et servir la page html créée précédemment à l’aide
d’un volume (option -v de docker run)
   
   > docker run --name Volumetest -p 80:80 -v /root/test:/usr/share/nginx/html:ro -d nginx
   
e. Supprimer le conteneur précédent et arriver au même résultat que
précédemment à l’aide de la commande docker cp
   
   >docker ps -a
   >docker rm -f Volumetest
   >docker cp /root/test/index.html mon_conteneur_id/usr/share/nginx/html

6. Builder une image

a. A l’aide d’un Dockerfile, créer une image (commande docker build)

   >FROM nginx:latest
   >COPY index.html /usr/share/html
   >docker build -t 
b. Exécuter cette nouvelle image de manière à servir la page html (commande
docker run)

   > docker run -p 90:80 nginx:latest

7. Utiliser une base de données dans un conteneur docker

a. Récupérer les images mysql:5.7 et phpmyadmin/phpmyadmin depuis le
Docker Hub

   > docker pull mysql:5.7
   > docker pull phpmyadmin
b. Exécuter deux conteneurs à partir des images et ajouter une table ainsi que
quelques enregistrements dans la base de données à l’aide de phpmyadmin

   > docker run --name mysql_container -p 3306:3306 -MYSQL_DATABASE=ynov -e MYSQL_USER=user -e MYSQL_PASSWORD=ihsan -e MYSQL_ROOT_PASSWORD=ihsan -d mysql:5.7
   > docker exec -it mysql_container bash
   > docker ps
   > docker start phpmyadmin_containe
   > ajout table dans container - methode graphique depuis l'interface
   > docker exec -it id_mysql -u root -p
