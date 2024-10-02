# Étape 1 : Construction de l'image
FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build

# Définir le répertoire de travail
WORKDIR /app

# Copier le fichier de projet et restaurer les dépendances
COPY src/Worker/Worker.csproj ./Worker/
RUN dotnet restore ./Worker/Worker.csproj

# Copier le reste des fichiers de l'application
COPY . .

# Construire l'application
RUN dotnet publish ./Worker/Worker.csproj -c Release -o out

# Étape 2 : Création de l'image finale
FROM mcr.microsoft.com/dotnet/runtime:3.1 AS runtime

# Définir le répertoire de travail
WORKDIR /app

# Copier les fichiers construits depuis l'étape de construction
COPY --from=build /app/out .

# Commande à exécuter lors du démarrage du conteneur
ENTRYPOINT ["dotnet", "Worker.dll"]
