# Windows 10 Universal C Runtime Requirement (Pre-Windows 10 only)
Windows 10 Universal C Runtime is required for mssql for Visual Studio Code to function propertly on older version of Windows. This is a known issue in the .NET Core project.
See [.NET Core Pre-reqs](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) for more detail.

## mssql extension support for Windows versions

|Windows version | Supported | Need to install the pre-req?|
|---|---|---|
|Windows 10|YES|NO|
|Windows Server 2016|YES|NO|
|Windows 8 and 8.1|YES|YES if not installed already|
|Windows Server 2012|YES|YES if not installed already|
|Windows 7|YES|YES if not installed already|
|Windows Server 2008 R2|YES|YES if not installed already|



## Instruction to install the pre-req for the mssql extension

1. [Download WindowsUCRT.zip](https://www.microsoft.com/en-us/download/details.aspx?id=48234) (7.7MB) and extract it to a folder.
2. Run the installer (.MSU) targeting your current OS configuration.