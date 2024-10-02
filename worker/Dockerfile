FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /app

COPY ./src/Worker/Worker.csproj ./Worker/
WORKDIR /app/Worker
RUN dotnet restore Worker.csproj

COPY ./src/Worker/ .
RUN dotnet publish -c Release -o /out Worker.csproj

FROM mcr.microsoft.com/dotnet/core/runtime:3.1 AS runtime
WORKDIR /app
COPY --from=build /out ./
ENTRYPOINT ["dotnet", "Worker.dll"]
