# Getting Started
Welcome! The mssql extension turns Visual Studio Code into a powerful development environment and code editor for Microsoft SQL Server, Azure SQL Databases and Data Warehouse evrywhere on Windows, Linux and macOS of your choice.

In this step-by-step tutorial, we will walk you through how to:
* Connect to Microsoft SQL Server, Azure SQL Databases and Data Warehouses.
* Easily write T-SQL script with IntelliSense, T-SQL snippets, syntax colorization, real-time error validation and more!
* Execute the script against the connected database.
* View the result in a slick grid.
* Save the result to a json or csv file format.

At the end, you will have a complete SQL Server development environment on your Windows, Linux or macOS. With that, you will be fully ready to venture into the exciting world of database development for your application.

### Step 1. Download and install mssql extension from Visual Studio Code marketplace.
* First, install [Visual Studio Code](https://code.visualstudio.com/#alt-downloads) and start it.
* Then install the mssql extension by pressing ```cmd+shift+p``` or ```F1``` to open the command palette in Visual Studio Code, select ```Install Extenion``` and choose ```mssql```.
    * For macOS, you will need to install OpenSSL which is a pre-requiste for DotNet Core that mssql extention uses. Follow the 'install pre-requisite' steps in [DotNet Core instruction page](https://www.microsoft.com/net/core#macos).
    * Or, simply run the following commands in your macOS Terminal.
        ```bash
        brew update
        brew install openssl
        ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
        ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
        ```
* If you don't have SQL Server, Azure SQL Database or Data Warehouse to connect to yet, get [Microsoft SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads), [Azure SQL Database](https://azure.microsoft.com/en-us/documentation/articles/sql-database-get-started) or [Data Warehouse](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-get-started-provision) then continue to Step 2. Don't forget [SQL Server 2016 Developer Edition](https://www.microsoft.com) or [SQL on Linux](https://www.microsoft.com) and its [Docker container for macOS](https://www.microsoft.com) is free to use.

### Step 2. Open a new or existing *.sql file
* Press ```cmd+n```. Visual Studio Code opens a new 'Plain Text' file by default. Press ```cmd+k,m``` and change the language mode to ```SQL```. 
* Or simply open a file with a .sql file extension. 
* The mssql extension looks for 'SQL' file type in the editor and activates commands and T-SQL IntelliSense on the .sql file. 

### Step 3. Create a new connection profile
To make a connection to SQL Server, Azure SQL Databases or Data Warehouse, you need a connection profile which defines connection properties such as the server name, database name and user name. The mssql extension has a built-in wizard in the command palette that will help to create a new connection profile. 

* Press ```F1```, and select ```MS SQL: Manage Connection Profile```. You can simply type ```sqlman``` and press ```enter```. Select ```Create```.
* ```Create``` task will walk you through a few questions.
    * **Server Name**: type in your SQL Server instance name or type ```localhost``` if it is running on your local machine. To connect Azure SQL Database or Data Warehouse, get the server name from the [Azure portal](https://portal.azure.com). Typically, it is ```<your-server-name>.database.windows.net``` format.
    * **Database Name**: Type in the name of database your want to connect. If you don't specify and press ```enter```, mssql will use the default value that is defined in the server such as ```master``` or ```tempdb``` for SQL Server. 
    * **Authentication Type**: If you run Visual Studio Code on Windows, the mssql extension will ask this question. Select ```SQL Login``` for this tutorial. On Linux and macOS, ```SQL Login``` is the only choice, hence the mssql extension will skip asking this question.
    * **User name**: Type a valid user name for the SQL Server instance you will connect to.
    * **Password**: Type a valid passowrd for the user.
    * **Save Password**: Select ```Yes```. The mssql extension securely stores the password in a secure store, for example KeyChain on macOS and get the password from KeyChain for the subsequent connections.
    * **Profile Name**: Type ```mssqlTutorial``` or a name that you like. Providing a name to a connection profile will help you search it later when you have multiple connection profiles.
    * Check if the connection profile is successfully created.

    If you want to use editor to manually create a connection profile or edit existing connection profiles, see [manage connection profiles wiki page](ManageConnectionProfiles.md). Knowing this way can be handy if you want to copy an existing connection profile, paste then edit it to create multiple connection profiles or to define advanced connection properties.

## Step 4. Connect!
* Press ```F1``` then type ```sqlcon``` or use ```cmd+shift+c``` shortcut to run ```MS SQL: Connect``` command. 
* Then select the connection profile ```mssqlTutorial``` and press ```enter```. 
* Check if the connection was successful. You can view the connection status on the status bar.

    [image connection status] 

## Step 5. Write T-SQL script
* In the editor, type ```sql```. It will show the list of T-SQL snippets. Keep typing in ```sqlcreate``` and select ```sqlCreateDatabase```.
    [image for snippet]
* Type a database name in the snippet generated script in the editor, let's use ```ClinicDB``` for this tutorial. It will look like:
    ```sql
    -- Create a new database called 'Clinic'
    -- Connect to the 'master' database to run this snippet
    USE master
    GO
    -- Drop the database if it already exists
    IF EXISTS (
        SELECT name
        FROM sys.databases
        WHERE name = N'Clinic'
    )
    DROP DATABASE Clinic
    GO
    -- Create the new database
    CREATE DATABASE Clinic
    GO
    ```

* Type the following T-SQL query. As you type, IntelliSense will help you coding with suggestions and auto-completion. The mssql extension also validates the query for an error.
    ```sql
    SELECT * FROM sys.databases WHERE name = N'Clinic';
    GO

    SELECT
        c.session_id, c.net_transport,
        c.auth_scheme, s.program_name,
        s.client_interface_name, s.login_name, 
        c.connect_time, s.login_time
    FROM sys.dm_exec_connections AS c
        JOIN sys.dm_exec_sessions AS s
        ON c.session_id = s.session_id
    WHERE c.session_id = @@SPID;
    GO
    ```

### Step 6. Execute
* Press ```F1``` then type ```sqlex``` or use ```cmd+shift+e``` to run ```MS SQL: Execute Query``` command. If you want to change the shortcut to a simpler or somthinge familiar to you such as ```F5``` or ```cmd+enter```, you can customize it. See [customizing keyboard shortcuts wiki page](CustomizingKeyboardShortcuts.md).

### Step 7. View and Save the result
* You will see ```CREATE DATABASE``` statement execution result in the Messages and ```SELECT``` query result in the Results.
* Try different split view layouts, horizontal and vertial. Running Visual Studio Code menu ```View``` --> ```Toggle Editor Group Layout``` to switch the layout.
* Play with following actions on the result view:
    * Click ```Results``` bar to toggle collapse and expand.
    * Click ```Messages``` bar to toggle collapse and expand.
    * Click ```Maximize / Restore``` icon button on a grid.
    * See [customize result view shortcuts wiki page](CustomizingResultViewShortcuts.md) for more actions and customizable shortcuts.
* Click the right mouse button on a grid to pop-up the result grid menu and run ```Select all```. 
* Click the right mouse button on a grid then run ```Save as JSON``` or click its icon button on the right side of the grid.
* Type a file name such as ```myfile.json```. It will save the result as a .json file format and open the file in the editor.

[image for playing with result view]

### Step 8. Use Database command and see the recent connection list
* Open a new file by pressing ```cmd+n``` then change the language mode to ```SQL``` by pressing ```cmd+k,m``` and type ```SQL```.
* Press ```F1``` and type ```sqlcon``` and select ```mssqlTutorial``` connection profile. Press ```enter``` to connect.
* Press ```F1``` and type ```sqluse``` or use ```cmd+shift+u``` to run ```MS SQL: Use Database``` command. Then select ```Clinic``` from the database list to switch the connection to ```Clinic``` database from master.
* Press ```F1``` and type ```sqlcon``` and press ```enter```. You will see a new connection entry is added for the ```Clinic``` database. The mssql extension keeps the history of recent connections automatically. Next time, you can simply browse and select the newly added recent connection to connect to the ```Clinic``` database. 

### End of tutorial and play more by yourself
Great! You have finished learning core features of the mssql extension. Play more with the sample T-SQL script below. Also explore other mssql features. Press ```F1``` and type ```mssql``` or ```sql``` to see the all supported commands from the mssql extension.
```sql
    -- Create Patients table
    CREATE TABLE [dbo].[Patients]
    (
        [PatientId] [int] NOT NULL,
        [FirstName] [nvarchar](50) NOT NULL,
        [LastName] [nvarchar](50) NOT NULL, 
        [Email] [nvarchar](50) NOT NULL,
        [City] [nvarchar](50) NULL,
        [MobileNumber] [nvarchar](50) NOT NULL
        PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY]
    );
    GO

    -- Insert sample data into Patients table
    INSERT INTO [dbo].[Patients]([PatientId],[FirstName],[LastName],[Email],[City],[MobileNumber])
    VALUES
        (1, 'Amitabh', 'Bachchan', 'angry_young_man@gmail.com', 'Mumbai', '2620616212'),
        (2, 'Abhishek', 'Bachchan', 'abhishek@abhishekbachchan.org', 'Mumbai', '8890195228'),
        (3, 'Aishwarya', 'Rai', 'ash@gmail.com', 'Mumbai', '9991206339'),
        (4, 'Joe', 'Blogger', 'joe@blogger.org', 'Mumbai', '8988234567'),
        (5, 'Sally', 'Parker', 'sallyp@gmail.org', 'Pune', '8008123456'),
        (6, 'Kareena', 'Kapoor', 'bebo@kapoor.org', 'Mumbai', '8007891721')
    GO

    -- Query Patient records
    SELECT [FirstName], [LastName], [Email], [MobileNumber] FROM Patients;
    GO
```
