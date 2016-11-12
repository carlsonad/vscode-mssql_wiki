## If you've experienced a SQL Tools Service crash

Report issues to [Github Issue Tracker] and let us know any details that will help reproduce the error.  Please leave a comment on existing issues so we can gauge how frequently those problems are occurring.

## Known Issues

* The mssql extension process may crash due to a bug in the product. It requires to restart VS Code to recover. Before restarting VS Code, please save your files.

* Installation Prerequisites: this extension requires the user to install some components needed by .Net Core applications, since this is used for connectivity to SQL Server.

    * For Mac OS, see [OpenSSL requirement on macOS]

    * For Windows 8.1, Windows Server 2012 or lower, see [Windows 10 Universal C Runtime requirement]

* Process is terminated due to StackOverflowException.

    * There is a bug in the SQL Parser which can be triggered by certain T-SQL syntax.  Please disable diagnostics if you hit this issue using the following user setting **"mssql.intelliSense.enableErrorChecking": false**. 

[GitHub Issue Tracker]:https://github.com/Microsoft/vscode-mssql/issues
[OpenSSL requirement on macOS]:https://github.com/Microsoft/vscode-mssql/wiki/OpenSSL-Configuration
[Windows 10 Universal C Runtime requirement]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement