This project is created from the .NET 6 Class Library project template.

# Project Preparation:

1) Configure the project build settings to include the Solution name in all namespaces:
 - Right click on the project and open the Properties menu item.
 - Under the Application | General tab, scroll down to the Assembly Name item.  Change the
 value to $(SolutionName).$(MSBuildProjectName)
 - Scroll down to the Default Namespace item immediately below Assembly Name.  Change the
 value to $(SolutionName.Replace(" ", "_")).$(MSBuildProjectName.Replace(" ", "_"))

2) Prepare project structure folders:

 - \Models
 - \Models\Base
 - \Models\Interfaces
