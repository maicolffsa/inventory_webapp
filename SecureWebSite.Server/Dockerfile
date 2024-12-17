# Usa la imagen oficial de .NET SDK para la construcción
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

WORKDIR /app

# Copia los archivos y restaurar dependencias
COPY ./*.csproj ./
RUN dotnet restore

# Copia el código fuente y construye la aplicación
COPY ./ ./
RUN dotnet publish -c Release -o /app/out

# Usa la imagen runtime para la ejecución
FROM mcr.microsoft.com/dotnet/aspnet:8.0

WORKDIR /app

# Copia los archivos construidos
COPY --from=build /app/out ./

# Expón el puerto 5000
EXPOSE 5003

# Ejecuta la aplicación .NET
ENTRYPOINT ["dotnet", "SecureWebSite.Server.dll"]