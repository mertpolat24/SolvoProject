# Build a�amas�
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app

# Proje dosyalar�n� kopyala
COPY Solvo-Web/*.csproj ./Solvo-Web/
RUN dotnet restore ./Solvo-Web/Solvo-Web.csproj

COPY . .
RUN dotnet publish ./Solvo-Web/Solvo-Web.csproj -c Release -o /app/publish

# Runtime a�amas�
FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build /app/publish .

# Uygulamay� ba�lat
ENTRYPOINT ["dotnet", "Solvo-Web.dll"]
