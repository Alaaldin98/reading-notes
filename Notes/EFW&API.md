# Entity Framework Core

Entity Framework (EF) Core is a lightweight, extensible, open source and cross-platform version of the popular Entity Framework data access technology.

EF Core can serve as an object-relational mapper (O/RM), which:

- Enables .NET developers to work with a database using .NET objects.
- Eliminates the need for most of the data-access code that typically needs to be written.
- EF Core supports many database engines, see Database Providers for details.

## SQL Server Express LocalDB
The connection string specifies SQL Server LocalDB. LocalDB is a lightweight version of the SQL Server Express Database Engine and is intended for app development, not production use. LocalDB starts on demand and runs in user mode, so there's no complex configuration. By default, LocalDB creates .mdf DB files in the C:/Users/<user> directory.

## Initialize DB with test data
EF creates an empty database. In this section, a method is added that's called after the database is created in order to populate it with test data.

>The EnsureCreated method is used to automatically create the database. In a later tutorial, you see how to handle model changes by using Code First Migrations to change the database schema instead of dropping and re-creating the database.


## The Model
With EF Core, data access is performed using a model. A model is made up of entity classes and a context object that represents a session with the database. The context object allows querying and saving data.





## Querying
Instances of your entity classes are retrieved from the database using Language Integrated Query (LINQ). 

## Saving data
Data is created, deleted, and modified in the database using instances of your entity classes.

## Data Seeding

Data seeding is the process of populating a database with an initial set of data.

There are several ways this can be accomplished in EF Core:

- Model seed data
- Manual migration customization
- Custom initialization logic

### What is User secrets? 
User secrets is a secure way of storing private user information such as API keys, client secrets, and connection strings. Essentially anything that you don’t want others to know about when using your code base.

>The user secrets is not uploaded to any source control. This ensures your keys do in fact stay “secret” to your local machine.