#### Create sepearte Cursor Application

##### Create a seperate Cursor profile on mac

```shell
cp -r ~/.cursor ~/.cursor-search
```

##### Automator

Open Automator. Create a new application and select "Run Shell Script". Select "/bin/bash" and then copy the following code:

```shell
#!/bin/bash

open -a Cursor --args --user-data-dir="$HOME/.cursor-search" --extensions-dir="$HOME/.cursor-search/extensions"
```

#### External App

##### Install Extension

Install "Open in External App" extension from VSCode marketplace:

```
YuTengjing.open-in-external-app
```

##### Settings Configuration

Add this configuration to your `settings.json`:

```json
{
  "openInExternalApp.openMapper": [
    {
      "extensionName": "md",
      "apps": [
        {
          "title": "Open in Obsidian",
          "shellCommand": "open \"obsidian://open?vault=obsidian&file=${fileBasenameNoExtension}\""
        }
      ]
    }
  ]
}
```

##### Keyboard Shortcut Setup

Add this to your `keybindings.json` for `Cmd+O` shortcut:

```json
{
  "key": "cmd+o",
  "command": "openInExternalApp.open",
  "when": "editorTextFocus && resourceExtname == '.md'"
}
```
