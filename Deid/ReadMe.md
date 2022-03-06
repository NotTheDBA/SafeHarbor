This project is created from the .NET 6 ASP.NET Core Web API project template, with Controllers enabled.

Remove the boilerplate sample code files before proceeding with project preparation:
 - In the root of the project, WeatherForecast.cs
 - In the \Controllers folder, WeatherForecastController.cs

# Project Preparation:

1) Configure the project build settings to include the Solution name in all namespaces:
 - Right click on the project and open the Properties menu item.
 - Under the Application | General tab, scroll down to the Assembly Name item.  Change the
 value to $(SolutionName).$(MSBuildProjectName)
 - Scroll down to the Default Namespace item immediately below Assembly Name.  Change the
 value to $(SolutionName.Replace(" ", "_")).$(MSBuildProjectName.Replace(" ", "_"))

2) Prepare project structure folders:
 - \Data
 - \Data\Migrations
 - \Data\Models

 3) Add a reference to the {SolutionName}.Common project.

 dotnet ef
 if not installed
	dotnet tool install --global dotnet-ef
 if version < 6.0.1 (or latest)
	dotnet tool update --global dotnet-ef

Install-Package Microsoft.EntityFrameworkCore.Tools
Install-Package Microsoft.EntityFrameworkCore.Design
Install-Package Microsoft.EntityFrameworkCore.SqlServer

dotnet ef migrations add InitialCreate
dotnet ef database update

dotnet user-secrets set ConnectionStrings:AppDb "Data Source=(localdb)\MSSQLLocalDB;Initial Catalog=Deid" --project deid

 Scaffold-DbContext "Data Source=(localdb)\MSSQLLocalDB;Database=deid;Trusted_Connection=True;" Microsoft.EntityFrameworkCore.SqlServer
  dotnet ef dbcontext scaffold Name=ConnectionStrings:AppDb Microsoft.EntityFrameworkCore.SqlServer --project deid --context-dir Data --output-dir Models --namespace SafeHarbor

 dotnet user-secrets set ConnectionStrings:AppDb "Data Source=(localdb)\MSSQLLocalDB;Initial Catalog=Deid"

 dotnet ef dbcontext scaffold Name=ConnectionStrings:AppDb Microsoft.EntityFrameworkCore.SqlServer --project deid --context-dir Data --output-dir Models --namespace SafeHarbor

 --context-namespace Your.DbContext.Namespace
