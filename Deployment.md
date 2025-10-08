cd ~/Examen_docker_L1C/ToDoList

nano Dockerfile # Creation du fichier Dockerfile

FROM nginx:alpine
COPY . /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"] # on doit voir cette contenu dans le dockerfile
Apres ctrl + o (Sauvegarder) puis entrer et ctrl + x pour quitter

ls -la # Pour voir le contenu du dockerfile

docker build -t todolist-app . # Pour construire l'image

docker run -d --name todolist-container -p 8080:80 todolist-app # Lancer le container

docker ps # Verifier le deployment

Pou terminer ouvrir dans le navigateur : http://localhost:8080
