# Manage connections in the **mssql** extension

### Available actions

| Action | Description |
|-----|-----|
| [**Create**](#create-a-new-connection) | Creates a new Connection using the Command Palette workflow |
| [**Clear recent connections list**](#clear-recent-connections-list) | Clears the list of recent connections. By default the 5 most recent connections to a database are shown in the connection list.  |
| [**Edit**](#edit-connections-in-the-user-settings-file)  | Opens the list of SQL connections stored in user settings |
| [**Remove**](#remove-a-connection-profile)  | Removes a connection profile from the user settings. Also removes any associated password saved in the password manager.  |

### Connection-related user preferences

| Preference | Description | Default Value |
|-----|-----|-----|
| **mssql.maxRecentConnections** | The maximum number of recent connections to be shown in the Connection list. | 5 |

See [Customize Options](customize-options) for a full list of extension preferences.

## Create a new connection
Connection setup is made easy using the **Connect** command. This helps you enter all the settings needed to connect to a SQL Server instance or database. 
Alternatively, you can add new connections directly to the user settings - hit **F1**, choose **MS SQL: Manage Connection Profiles**, then **Edit** to open the settings and copy & paste new connections.

### New connection from Command Palette
Type **F1**, then select the **MS SQL: Connect** command to open the connection workflow.
The following table describes the Connection Profile properties.

| Setting | Description |
|-----|-----|
| **Server name** | The SQL Server instance name. For this tutorial, use **localhost** to connect to the local SQL Server instance on your machine. If connecting to a remote SQL Server, enter the name of the target SQL Server machine or its IP address. |
| **[Optional] Database name** | The database that you want to use. For purposes of this tutorial, don't specify a database and press **enter** to continue. |
| **User name** | Enter the name of a user with access to a database on the server. For this tutorial, use the default **SA** account created during the SQL Server setup. |
| **Password (SQL Login)** | Enter the password for the specified user. | 
| **Save Password?** | Type **Yes** to save the password. Otherwise, type **No** to be prompted for the password each time the Connection Profile is used. |
| **[Optional] Enter a name for this profile** | The Connection Profile name. For example, you could name the profile **localhost profile**. |

> [!TIP] 
> See the [**Password management**](#password-management) section below for how passwords are stored when **Save Password** is chosen. 

### New connection from user settings
See the [**Editing Connections**](#edit-connections-in-the-user-settings-file) section for details on how to add new connections and edit existing connections in the user settings. 

## Clear recent connections list
Type **F1**, then select the **MS SQL: Manage Connection Profiles** command and choose **Clear Recent Connections List**. This will prompt you to clear the recent connections list.
Any saved connection profiles will still be shown when connecting, but databases connected to via the `USE` TSQL command or using the **MS SQL: USE Database** command in VSCode will
be cleared from the list

## Edit connections in the user settings file
1. Type **F1**, then select the **MS SQL: Manage Connection Profiles** command and choose **Edit**. This opens the user settings in VSCode.
2. Go to the **"mssql.connections"** section in settings.json. If you've never created a connection you'll need to add a line `"mssql:connections": []` to the settings file.
3. Add a new connection by typing `{ }`, then entering connection properties as shown in the example below. 

    ```javascript
    "mssql.connections": [
        {
            "authenticationType": "SqlLogin",
            "server": "myservername",
            "database": "optionalDbName",
            "user": "MyUserName",
            "password": "",
            "savePassword": true
        }
    ]
    ```

   > [!TIP] 
   > For **SqlLogin** authentication a password is required. We recommend leaving the `"password": ""` property empty and setting `"savePassword": true`. When you first connection, you will be prompted for your password which will then be
   saved separately. See the [**Password management**](#password-management) section below for details on how your passwords are stored.
4. Edit an existing connection in the same way - for example change the `"authenticationType"` property to `"Integrated"` to connect using Integrated Authentication on Windows 

### Additional Connection Properties
All connection properties supported by the ADO.Net driver for .Net Core are supported. 
Properties are in JSON object format, so to add new properties type `,` at the end of a connection object in the list.
Then use IntelliSense by typing `Ctrl+Space` to list the properties and values that can be set.

## Remove a connection profile
1. Type **F1**, then select the **MS SQL: Manage Connection Profiles** command and choose **Remove**. 
2. Select the profile you wish to remove from the profile list. When prompted choose `Yes` to remove the profile.
3. The selected connection profile and any linked password will be removed from the user settings and credential store.

## Password management
If you choose to save the password when connecting to a database, this is stored outside of your user or workspace settings in order to minimize the change that 
important credentials are accidentally checked into source control or made visible to other users on a shared computer. 

When you **Remove** a connection profile from the **Manage Connection Profiles** options any related password is also removed. 
If you manually deleted entries in the user settings, this is not automatically cleaned up. In this case, see instructions below on how to verify and clear your saved passwords.

| Operating System | Password Storage | How to clear Passwords |
|-----|-----| -----|
| **Windows** | Credentials are stored using the Windows Credential API. | Open the **Credential Manager** in **Control Panel**. Choose **Windows Credentials** and delete all credentials starting with `sqlsecret` |
| **Mac OS** | Credentials are stored using the Keychain | Open **Keychain Access** from the Launchpad. Search for `sqlsecret`. Select all credentials, control-click and choose **delete items** |
| **Linux** | Credentials are stored in a file ~/.sqlsecrets/sqlsecrets.json. Read/Write permissions are restricted to the current user. Note that users with sudo permissions may be able to read this file | Delete the `~/.sqlsecrets/sqlsecrets.json` file. |
