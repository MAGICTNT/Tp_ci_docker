# Étape de construction
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /app

# Copier le fichier csproj et restaurer les dépendances
COPY ./Worker/*.csproj ./Worker/
RUN dotnet restore ./Worker/Worker.csproj

# Copier le reste des fichiers et publier l'application
COPY ./Worker/. ./Worker/
RUN dotnet publish ./Worker/Worker.csproj -c Release -o out

# Étape de runtime
FROM mcr.microsoft.com/dotnet/core/runtime:3.1 AS runtime
WORKDIR /app
COPY --from=build /app/Worker/out ./
ENTRYPOINT ["dotnet", "Worker.dll"]
