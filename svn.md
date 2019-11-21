# Server commands
## Create a new repository
```svnadmin create <repository_name>```

# Client commands

## Repository info
```svn info svn://server_path:3960/<repository_name>```

# Configurations
To change the default editor for subversion, access the file ```~/.subversion/config``` in the section **[helpers]** and set the property **editor-cmd**:
```
[helpers]
editor-cmd = vim
```
