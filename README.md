Azure Test Apps
================

Contains test applications for testing on Azure.

1. Spin up an Azure Web App
   - `az login --service-principal -u <something> -p <pass> --tenant <tenant>`
   - `az account set --subscription <subscription id>`
   - `az group create --location westus2 --name <group>`
   - `az appservice plan create --name <name> --resource-group <group> --sku S1`
   - `az webapp create --name <name> --resource-group <group> --plan <name>`
2. Copy dotnet folder with store, shared runtime, sdk, and hostfxr to Web App (TODO: this wont work for testing older apps, we might need to copy 1.0.X and 1.1.X dotnet also)
3. Publish selected App from samples to Web App
   - `az webapp deployment slot create --name <name> --resource-group <group> --slot production`
   - `az webapp deployment source config --name <name> --resource-group <group> --slot production --repo-url <url> --branch <branch> --manual-integration --cd-app-type aspnetcore`
4. Set processPath in web.config in Web App to copied dotnet folder location
5. Wget/curl http://app/Home/About page and compare assembly load locations with expected values
6. Clean up
   - `az group delete --name <group> --yes`
   - `az logout`

This project is part of ASP.NET Core. You can find samples, documentation and getting started instructions for ASP.NET Core at the [Home](https://github.com/aspnet/home) repo.