# Getting Started

Welcome! The **mssql** extension turns Visual Studio Code into a powerful development environment and code editor for Microsoft SQL Server, Azure SQL Databases and Data Warehouses evrywhere on Linux, macOS and Windows of your choice.

In this tutorial, we will walk you through how to:

* Install Visual Studio Code and the **mssql** extension.

* Connect to SQL Server.

* Easily write T-SQL script with IntelliSense, TSQL snippets, syntax colorization and real-time error validations.

* Execute the script against the connected database.

* View the result in a slick grid.

* Save the result to a json or csv file format.

## Install Visual Studio Code
1. If you have not already installed Visual Studio Code, [Download and install VS Code](https://code.visualstudio.com/Download) on your Linux, macOS or Windows machine.

2. Start Visual Studio Code.

## Install the mssql extension
The following steps explain how to install the mssql extension. 

1. Press **ctrl+shift+p** (or **F1**) to open the command palette in Visual Studio Code, select **Install Extension** and type **mssql**.
    > [!TIP] 
    > For macOS, **cmd** key is equivalent to **ctrl** key on Linux and Windows.

2. Click install **mssql**. 
    
    <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-extension.png" alt="Install the extension" style="width: 300px;"/>

    > [!NOTE]
    > **vscode-mssql** is a prototype version and it will retire from Visual Studio Code Marketplace soon. If you have already installed the vscode-mssql extension, remove it.

3. The **mssql** extension takes up to one minute to install. Wait for the prompt that tells you it installed successfully.

    <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-install-success-notification.png" alt="Insatllation success notification" style="width: 480px;"/>

    > [!TIP]
    > For macOS, you will need to install OpenSSL which is a pre-requiste for DotNet Core that mssql extention uses. Follow the 'install pre-requisite' steps in [DotNet Core instruction page](https://www.microsoft.com/net/core#macos).
    > Or, simply run the following commands in your macOS Terminal.

    ```bash
    brew update
    brew install openssl
    ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
    ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
    ```

4. If you don't have SQL Server, Azure SQL Database or Data Warehouse to connect to yet, get [Microsoft SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads), [Azure SQL Database](https://azure.microsoft.com/en-us/documentation/articles/sql-database-get-started) or [Data Warehouse](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-get-started-provision) and continue this tutorial.

## Open a new or existing *.sql file
1. Press **ctrl+n**. Visual Studio Code opens a new 'Plain Text' file by default. Press **ctrl+k,m** and change the language mode to **SQL**. 

    <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-language-mode.png" alt="SQL language mode" style="width: 300px;" />

2. Or open a file with a .sql file extension. 

    > [!NOTE]
    > The **mssql** extension enables mssql commands and TSQL IntelliSense in the editor for a file with .sql extension or when the language mode is **SQL**.

## Connect to SQL Server

The following steps show how to connect to SQL Server with VS Code.

1. In VS Code, press **ctrl+shift+p** (or **F1**) to open the Command Palette.

2. Type 'sql' to display the mssql commands.

    <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-commands.png" alt="mssql commands" style="width: 480px;" />
   

3. Select the **MS SQL: Connect** command. You can simply type **sqlcon** and press **enter**.

4. Select **Create Connection Profile**. This creates a connection profile for your SQL Server instance.

5. Follow the prompts to specify a sequence of values for the new connection profile. After specifying each value, press **enter** to continue. 

    The following table describes the Connection Profile properties.

   | Setting | Description |
   |-----|-----|
   | **Server name** | The SQL Server instance name. For this tutorial, use **localhost** to connect to the local SQL Server instance on your machine. If connecting to a remote SQL Server, enter the name of the target SQL Server machine or its IP address. |
   | **[Optional] Database name** | The database that you want to use. For purposes of this tutorial, don't specify a database and press **enter** to continue. |
   | **User name** | Enter the name of a user with access to a database on the server. For this tutorial, use the default **SA** account created during the SQL Server setup. |
   | **Password (SQL Login)** | Enter the password for the specified user. | 
   | **Save Password?** | Type **Yes** to save the password. Otherwise, type **No** to be prompted for the password each time the Connection Profile is used. |
   | **[Optional] Enter a name for this profile** | The Connection Profile name. For example, you could name the profile **localhost profile**. 

    > [!Tip] 
    > You can create and edit connection profiles in User Settings file (settings.json). Open the settings file with **Preference**-->**User Settings** menu in VS Code. For more detail, see [manage connection profiles](sql-server-linux-connect-and-query-vs-code-manage-connection-profiles.md).

6. Press **esc** key to close the info message that informs you that the profile is created and connected

    > [!TIP]
    > If you get a connection failure, first attempt to diagnose the problem from the error message in the **Output** pannel in VS Code (**View** --> **Output** menu). Then review the [connection troubleshooting recommendations](sql-server-linux-connect-and-query.md#troubleshoot).

7. Verify your connection in the status bar.

   <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-connection-status.png" alt="Connection status" style="width: 300px;" />

## Create a database

1. In the editor, type **sql** to bring up a list of editable code snippets. 

   <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-sql-snippets.png" alt="SQL snippets" style="width: 480px;" />

2. Select **sqlCreateDatabase**.

3. In the snippet, type **TutorialDB** for the database name.

    ```sql
    USE master
    GO
    IF NOT EXISTS (
        SELECT name
        FROM sys.databases
        WHERE name = N'TutorialDB'
    )
    CREATE DATABASE [TutorialDB]
    GO
    ```
4. Press **ctrl+shift+e** to execute the Transact-SQL commands. View the results in the query window.

    <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-create-database-messages.png" alt="create database messages" style="width: 480px;" />

    > [!TIP]
    > You can customize shortcut key bindings for the mssql extension commands. See [customize shortcuts](./sql-server-linux-connect-and-query-vs-code-wiki-customize-shortcuts)

## Create a table

1. Remove the contents of the editor window.

2. Press **F1** to display the Command Palette.

3. Type **sql** in the Command Palette to display the SQL commands or type **sqluse** for **MS SQL:Use Database** command.

4. Click **MS SQL:Use Database**, and select the **TutorialDB** database. This changes the context to the new database created in the previous section.

    <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-use-database.png" alt="use database" style="width: 480px;" />

3. In the editor, type **sql** to display the snippets, and then select **sqlCreateTable** and press **enter**.

4. In the snippet, type **Employees** for the table name.

5. Press **Tab**, and then type **dbo** for the schema name.

    > [!NOTE]
    > After adding the snippet, you must type the table and schema names without changing focus away from the VS Code editor.

6. Change the column name for **Column1** to **Name** and **Column2** to **Location**.

    ```sql
    -- Create a new table called 'Employees' in schema 'dbo'
    -- Drop the table if it already exists
    IF OBJECT_ID('dbo.Employees', 'U') IS NOT NULL
    DROP TABLE dbo.Employees
    GO
    -- Create the table in the specified schema
    CREATE TABLE dbo.Employees
    (
        EmployeesId INT    IDENTITY(1,1)    NOT NULL    PRIMARY KEY, -- primary key column
        Name        [NVARCHAR](50)          NOT NULL,
        Location    [NVARCHAR](50)          NOT NULL
    );
    GO
    ```

7. Press **ctrl+shift+e** to create the table.

## Insert and query

1. Add the following statements using TSQL IntelliSense to insert four rows and then select all the rows from the **Employees** table.

    ```sql
    -- Insert rows into table 'Employees'
    INSERT INTO Employees
        ([Name],[Location])
    VALUES
        (N'Jared', N'Australia'),
        (N'Nikita', N'India'),
        (N'Tom', N'Germany'),
        (N'Jake', N'United States')   
    GO    
    -- Query the total count of employees
    SELECT COUNT(*) as EmployeeCount FROM dbo.Employees;
    -- Query all employee information
    SELECT e.EmployeesId, e.Name, e.Location 
    FROM dbo.Employees as e
    GO
    ```
    <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-intellisense.png" alt="TSQL IntelliSense" style="width: 480px;" />

2. Press **ctrl+shift+e** to execute the commands. The two result sets display in the Results window. 

    <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-result-grid.png" alt="Results" style="width: 300px;" />

    > [!TIP] 
    > For Linux, xclip is required for selection copy from the results grid.

## View and save the result

1. Select VS Code menu: **View** --> **Toggle Editor Group Layout** to switch to vertical or horizontal split layout.

    <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-toggle-split.png" alt="Vertical split" style="width: 480px;" />

2. Click the **Results** and **Messages** pannel header to collapse and expand the pannel.

    <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-toggle-messages-pannel.png" alt="Toggle Messages" style="width: 480px;" />

    > [!TIP]
    > You can customize the default behavior of the mssql extension such as your preference on the initial state of collapse and expand the Messages pannel and more. See [customize the mssql extension options](./sql-server-linux-connect-and-query-vs-code-wiki-customize-options) for more details.

2. Click the maximize grid icon on the second result grid to zoom in.

    <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-maximize-grid.png" alt="Maximize grid" style="width: 480px;" />

    > [!NOTE]
    > Maximize icon displays when your TSQL script has more than two result grids.

3. Open the grid context menu with the right moouse button on a grid. 

    <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-grid-context-menu.png" alt="Context menu" style="width: 480px;" />

4. Select **Save All**

5. Open the grid context menu and select **Save as JSON** to save the result to a .json file.

6. Specify a file name for the json file. For this tutorial, type **employees.json**.

7. Check the json file is saved and opened in VS Code.

    <img src="./media/sql-server-linux-connect-and-query-vs-code/vscode-save-as-json.png" alt="Save as Json" style="width: 480px;" />

## Next steps

In a real-world scenario, you might create a script that you need to save and run later (either for administration or as part of a larger development project). In this case, you can save the script with a **.sql** extension.

If you're new to T-SQL, see [Tutorial: Writing Transact-SQL Statements](https://msdn.microsoft.com/library/ms365303.aspx) and the [Transact-SQL Reference (Database Engine)](https://msdn.microsoft.com/library/bb510741.aspx).

For more information on using VS Code, see the [Visual Studio Code documentation](https://code.visualstudio.com/docs).
