## Pre-Requisites

Microsoft Visual Studio 2019 Community Edition

.net core 3 https://dotnet.microsoft.com/download/dotnet-core

MySQL Tools for Visutal Studio https://dev.mysql.com/downloads/windows/visualstudio/
	
mysql-for-visualstudio-1.2.9.msi (https://dev.mysql.com/downloads/windows/visualstudio/)
	
## Configurating ASP.NET Membership web app for MySQL

### Step 1:

 Delete Migrations Directory under the Data Directory

### Step 2:

Uninstall the package Microsoft.EntityFrameworkCore.SQLServer

Install the package Pomelo.EntityFrameworkCore.MySql

### Step 3:

Create db in MySql

> CREATE SCHEMA reactmembership;

### Step 4:

Update value of DefaultConnection in appsettings.json to 

> server=localhost;port=3306;database=reactmembership;user=root;password=p@$$w0Rd;CharSet=utf8

### Step 5:

In Startup.cs file update ConfigureServices method to replace UseSqlServer with UseMySql

### Step 6:

Tools-> Nuget Package Manager -> Package Manager Console

In Visual Studio, use the Package Manager Console to scaffold a new migration and apply it to the database:

> Add-Migration [migration name]

> Update-Database

Alternatively, you can scaffold a new migration and apply it from a command prompt at your project directory:

> dotnet ef migrations add [migration name]

> dotnet ef database update
