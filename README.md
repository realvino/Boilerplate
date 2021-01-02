# Clean Architecture Boilerplate - ASP.NET Core 5.0 (WebApi & MVC)
Clean Architecture Solution Template for ASP.NET Core 5.0. Built with Onion/Hexagonal Architecture and incorporates the most essential Packages your projects will ever need. Includes both WebApi and Web(MVC) Projects.

Getting Started With ASP.NET Core Hero Boilerplate
Let’s install the required the NuGet Package First. The download size is around 10 Mb. Open up Command Prompt and run the following command.

dotnet new --install AspNetCoreHero.Boilerplate
Now what this does is, it installs the entire Solution Template on to your machine so that you can use the template as a starting point for your upcoming projects. Let’s see how to start generating solutions and configure them.

Navigate to your Repository folder (any folder where you usually create your projects). Open up your command prompt and change the directory to your working folder. For this demonstration, I am going to create a WebApplication Solution for a Store. I will be naming it StoreManager and use the location as ‘D:\Repository\’.

cd D:\Repository\

Next, type in the following command to actually generate the Solution with your required Namespace. For this demonstation, I am using the name StoreManager.

dotnet new aspnetcorehero.boilerplate -n StoreManager

Once the Packages are done restoring, open up the appsettings.json of both the API and MVC Projects. Make sure that you add in valid Connection strings here. Here is how I set it up for my database server (MSSQL).

"ConnectionStrings": {
  "ApplicationConnection": "Data Source=LAPTOP-7CS9KHVQ;Initial Catalog=StoreManager;Integrated Security=True;MultipleActiveResultSets=True",
  "IdentityConnection": "Data Source=LAPTOP-7CS9KHVQ;Initial Catalog=StoreManager;Integrated Security=True;MultipleActiveResultSets=True"
},

Once the Connection Strings are updated, let’s add the Migrations and Update the Database. Open up package Manager Console and Set the Startup project as the API Project. Set the Default Project as the Infrastructure project (See the red highlighted area in the screenshot below). Run the following commands.


add-migration initial2 -context ApplicationDbContext

add-migration initialIdentity2 -context IdentityContext


Note that I have already added the Migrations to the Solution Template, which means you really don’t have to do the above mentioned step to generate the Migrations. But in case you lose the Migration file, use the above commands to regenrate them.

With the Migrations ready, let’s update the database now.


update-database -context IdentityContext

update-database -context ApplicationDbContext


Default Roles & Credentials:

As soon you build and run your Awesome Application, default users and roles get added to the database.

Default Roles are as follows.


SuperAdmin
Admin
Moderator
Basic

Here are the credentials for the default users.


Email – superadmin@gmail.com / Password – 123Pa$$word!

Email – basic@gmail.com / Password – 123Pa$$word!
