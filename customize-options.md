# Customizing Options

The mssql extension allows you to customize the extension settings in your VS Code workspace or user settings. All mssql options begin the prefix 'mssql' and are in json format. 

## Access User and Workspace Settings
To access settings, go to File > Preferences (Code > Preferences on Mac) and choose user or workspace settings. You can place your settings in the settings.json file that opens. Modifying and saving this file will overwrite the default settings.

User settings apply globally to any VS Code instance you open. Workspace settings apply only within a workspace that is opened.

You can learn more about vscode user and workspace settings [here.](https://code.visualstudio.com/Docs/customization/userandworkspace)
## Extension Options

### Log debug information to console
When set to true, logs debug output to the VS Code console  
**Setting** : *mssql.logDebugInfo*  
**Default Value** : *false*  
**Example**  
```json
    "mssql.logDebugInfo": true
```

### Keyboard shortcuts for the results window
Customize keyboard shortcuts related to the results window. 
Ctrl represents ctrl on windows/linux and cmd on mac. *Some key combinations might not work with these events because they overlap with shortcuts.*
You can find out more about customizing shortcuts [here.](https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts#other-shortcuts)  
**Setting** : *mssql.shortcuts*  
**Default Value** :   
>*event.toggleResultPane - ctrl+alt+r*  
>*event.toggleMessagePane - ctrl+alt+y*  
>*event.prevGrid - ctrl+up*  
>*event.nextGrid - ctrl+down*  
>*event.copySelection - ctrl+c*   


**Example**  
```json
    "mssql.shortcuts": {
        "event.toggleResultPane": "ctrl+alt+r",
        "event.toggleMessagePane": "ctrl+alt+y",
        "event.prevGrid": "ctrl+up",
        "event.nextGrid": "ctrl+down",
        "event.copySelection": "ctrl+c",
        "event.toggleMagnify": "ctrl+alt+m",
        "event.selectAll": "ctrl+alt+a",
        "event.saveAsJSON": "ctrl+alt+j",
        "event.saveAsCSV": "ctrl+alt+c"
    }
```
### Save results as CSV - include headers
You can choose to include or exclude column headers in the CSV file with the `includeHeaders` setting.  When set to true, the headers are included in the saved CSV file.  
**Setting** : *mssql.saveAsCSV*  
**Default Value** :   
>*includeHeaders - true*  


**Example**  
```json
    "mssql.saveAsCsv": {
        "includeHeaders": true
    }
```

### Open messages pane by default in the results window
When set to true, keeps the messages pane open default in the results window.  
**Setting** : *mssql.messagesDefaultOpen*  
**Default Value** : *true*  
**Example**  
```json
    "mssql.messagesDefaultOpen": false
```


### Connection settings
You can find out how to set connection information in your settings [here](https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles#edit-connections-in-the-user-settings-file).