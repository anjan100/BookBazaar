**BookBazaar – Book Library System**
**BookBazaar** is an all-in-one online book retail platform with in-store pickup capabilities, developed using **ASP.NET Core Web API and Razor Pages.**
It enables secure member logins, catalog filtering, cart and order management, bookmarking, and provides an admin dashboard to manage books, discounts, and announcements.

## Tech Stack

| Layer       | Tech                                    |
|-------------|-----------------------------------------|
| API         | ASP.NET Core 8 Web API                  |
| Front End   | Razor Pages MVC Web App                 |
| Database    | Entity Framework Core with SQL Server   |
| Auth        | JWT (Admin/Member Roles)                |
| UI Styling  | CSS/Bootstrap 5                         |

---
## Prerequisites

- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- Visual Studio 2022+ with ASP.NET and EF Core workloads
- SQL Server (Express or LocalDB)
- EF Core CLI tools:
  ```bash
  dotnet tool install --global dotnet-ef
  

**Running the Project**

**1. Open the Solution**
Open BookBazaarProject.sln in Visual Studio.

**2. Set Both Projects to Run Simultaneously**
Right-click the Solution (BookBazaar) > properties>  Set Startup Projects

Choose Multiple startup projects: Set both BookBazaarAPI and BookBazaarWeb to Start
This ensures pressing F5 runs both backend and frontend together.

**3. Configure SQL Server Connection**
In BookBazaarAPI/appsettings.json, set database connection:

 "ConnectionStrings": {
     "DefaultConnection": "Server=DESKTOP-GH4LHNL\\SQLEXPRESS;Database=BookBazaarDB;Trusted_Connection=True;TrustServerCertificate=True;"
 },

Replace the Server name if needed (e.g. localhost\\SQLEXPRESS, or your machine's SQL instance).

Open Microsoft SQL Server Management studio.

**4. Apply Migrations (First Run Only)**
To generate database tables:

cd LibraryAPI
dotnet ef database update


This applies the latest schema migration and creates BookBazaarDB.
If not created manually create database BookBazaarDB in Microsoft SQL Server Management studio.

**5. Run the App**
From Visual Studio:
Press F5 (or Ctrl + F5) and both projects will run.

Or run individually:

```cd LibraryAPI
dotnet run

cd ../LibraryWeb
dotnet run
API: https://localhost:7110

Web: https://localhost:7171
```

**Admin Setup**
By default, all registered users are Members. To promote one to Admin, run this SQL:

UPDATE Members SET IsAdmin = True for Email = 'admin@example.com';


