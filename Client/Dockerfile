FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app

COPY Client.csproj .
RUN dotnet restore Client.csproj
EXPOSE 11000

COPY . .
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/runtime:6.0 AS runtime
WORKDIR /app
COPY --from=build /app/out ./

ENTRYPOINT ["dotnet", "Client.dll"]