# Stage 1: Build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

WORKDIR /src

# Step 1: copy project file
COPY src/dotnet-demoapp.csproj ./

# Step 2: restore dependencies
RUN dotnet restore

# Step 3: copy remaining source code
COPY src/. ./

# Step 4: publish app
RUN dotnet publish -c Release -o /app/publish

# Stage 2: Runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0

WORKDIR /app
COPY --from=build /app/publish .

EXPOSE 5000
CMD ["dotnet", "dotnet-demoapp.dll"]
