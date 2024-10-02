# Utiliser l'image de base Node.js
FROM node:14

# Définir le répertoire de travail
WORKDIR /app

# Copier package.json et package-lock.json
COPY package*.json ./

# Installer les dépendances
RUN npm install

# Copier le reste des fichiers de l'application
COPY . .

# Exposer le port sur lequel l'application écoute (ajuster selon besoin)
EXPOSE 3000

# Commande pour lancer l'application
CMD ["node", "server.js"]
