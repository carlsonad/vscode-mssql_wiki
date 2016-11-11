# Customize Keyboard Shortcuts

The vscode mssql extension offers various keyboard shortcuts which can be customized through 
vscode itself or through a user preference for the extension.

## Through Vscode

`extension.runQuery`

This command runs a query for the current active document if that document has a language id
of `sql`. By default this command is bound to `ctrl+shift+e` on windows and linux and 
`cmd+shift+c` on mac.

`extension.connect`

This command connects the current active document to a sql server. By default this command is
bound to `ctrl+shift+c` on windows and linux and `cmd+shift+c` on mac.

`extension.disconnect`

This command disconnects the current active document. By default this command is bound to
`ctrl+shift+d` on windows and linux and `cmd+shift+d` on mac.

`extension.chooseDatabase`

This command opens a prompt to change the active database for the current active document. By
default this command is bound to `ctrl+shift+u` on windows and linux and `cmd+shift+u` on mac.

### Sample scenario: customize MS SQL: Execute Query command shortcut

1. Go to VS Code menu **Preferences**-->**Keyboard Shortcuts**. 

2. It opens **Default Keyboard Shortcuts** file and **keybindings.json** file.

3. Press **F3** in Default Keyboard Shortcuts file and find a command to customize. For this sample scenario, type **extension.runQuery**.

4. Copy extension.runQuery keybinding definition from Default Keyboard Shortcuts file.

5. Paste to keybindings.json file and change the value for the "key" property to "F5". 

```javascript
// Place your key bindings in this file to overwrite the defaults
[
   { "key": "F5",           "command": "extension.runQuery",
                            "when": "editorTextFocus && editorLangId == 'sql'" }
]
```

6. Save keybindings.json file and try the new shortcut.

> Note that you may override the shortcut for another command. For example, F5 is Launch command in the debugging session. Choose a keybinding with this consideration.

## Other Shortcuts

The extension offers other shortcuts related to the results pane through the user settings of
the extension. These can be customized through the extension setting `mssql.shortcuts`. When
customizing these shortcuts use `ctrl` is represent both the ctrl key on windows and linux,
but also the cmd key on mac, i.e `ctrl+l` for ctrl+l on windows and linux and cmd+l on mac.
Important note: some keyboard shortcuts will not work with these events. Known shortcuts that
don't work: `(ctrl|cmd)+a` on all platforms, `cmd+m` on mac (interfers with a native mac 
shortcut).

`event.toggleResultPane`

This event toggles the collapse of the results pane if the results window is the active window. 
By default this command is bound to `ctrl+alt+r` on windows and linux and `cmd+alt+r` on mac.

`event.toggleMessagePane`

This event toggles the collapse of the message pane if the results window is the active window.
By default this command is bound to `ctrl+alt+y` on windows and linux and `cmd+alt+y` on mac.

`event.prevGrid`

This event changes the active grid to the previous grid (above) if the results window is the
active window. By default this command is bound to `ctrl+up arrow` on windows and linux and
`cmd+up arrow` on mac.

`event.nextGrid`

This event changes the active grid to the next grid (below) if the results window is the
active window. By default this command is bound to `ctrl+down arrow` on windows and linux
and `cmd+down arrow` on mac.

`event.copySelection`

This event copies the current selection from the current active grid if the results window
is the active window. By default this command is bound to `ctrl+c` on windows and linux and
`cmd+c` on mac.

`event.maximizeGrid`

This event maximizes and minimizes the current active grid if the results window is the active
window. By default this command is unbound.

`event.selectAll`

This event selects the entire data set for the active grid if the results window is the active
window. By default this command is unbound.

`event.saveAsJSON`

This event saves the data from the current active grid if the results window is the active 
window data as a local JSON file. By default this command is unbound.

`event.saveAsCSV`

This event saves the data from the current active grid if the results window is the active 
window data as a local CSV file. By default this command is unbound.