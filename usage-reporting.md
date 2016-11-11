# Usage Reporting
Microsoft collects data to operate effectively and provide you with the best experiences with our products. This includes mssql for Visual Studio Code.

Your privacy is important to us. The [Privacy Statement](https://www.microsoft.com/en-us/privacystatement/EnterpriseDev/default.aspx) explains what data we collect from you and how we use it.

## What is collected and reported?
We collect data about how mssql for Visual Studio Code is used as well as how it interacts with other Microsoft products and services. Broadly speaking, we collect the following types of usage data:
* **Product use data**. We collect data about the features you use, how often you use them, and how you use them.
* **Device data**. We collect data about your device. This includes data about operating systems and other software installed on your device, including version information.
* **Error reports and performance data**. We collect data about the performance of mssql for Visual Studio Code and any problems you experience with it. This data helps us improve our products and services, to diagnose problems you see, and provide solutions.

For specifics on what data is collected, you can view the [source code of mssql for Visual Studio Code](https://github.com/microsoft/vscode-mssql) for the most up-to-date and accurate information. Search for references to `Telemetry.sendTelemetryEvent` within the source code to learn more. Each call to this method represents a unique event that we track, and parameters provide information on the data points that are collected as part of the event.

Additionally, we rely upon the following Node.js modules from Microsoft for providing data collection services. Please consult the source code of these modules for more information on common properties we collect with every event:
* [vscode-extension-telemetry](https://github.com/Microsoft/vscode-extension-telemetry) 
* [ApplicationInsights] (https://github.com/Microsoft/ApplicationInsights-node.js)

## How to turn off sending usage reports to mssql for Visual Studio Code team
By default, we collect usage data from mssql for Visual Studio Code. If you would like to disable the collection of usage data, please see the following:
[Visual Studio Code FAQ: How to disable telemetry reporting](https://code.visualstudio.com/Docs/supporting/faq#_how-to-disable-telemetry-reporting). We respect the preference you provide Visual Studio Code in the user settings.