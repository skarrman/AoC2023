FROM mcr.microsoft.com/dotnet/sdk:8.0-alpine AS build

# build application 
WORKDIR /src
COPY . .
RUN dotnet restore
RUN dotnet publish -c release -o /app --no-self-contained --no-restore

# final stage/image
FROM mcr.microsoft.com/dotnet/runtime:8.0-alpine

WORKDIR /app
COPY --from=build /app .
COPY input.txt .

ENTRYPOINT ["./day17"]