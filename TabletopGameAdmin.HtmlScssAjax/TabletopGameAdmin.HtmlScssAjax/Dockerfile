#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /src
COPY ["TabletopGameAdmin.HtmlScssAjax/TabletopGameAdmin.HtmlScssAjax.csproj", "TabletopGameAdmin.HtmlScssAjax/"]
RUN dotnet restore "TabletopGameAdmin.HtmlScssAjax/TabletopGameAdmin.HtmlScssAjax.csproj"
COPY . .
WORKDIR "/src/TabletopGameAdmin.HtmlScssAjax"
RUN dotnet build "TabletopGameAdmin.HtmlScssAjax.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "TabletopGameAdmin.HtmlScssAjax.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "TabletopGameAdmin.HtmlScssAjax.dll"]