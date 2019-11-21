# Server commands
## Create a new repository
```svnadmin create <repository_name>```

# Client commands

**Repository info**

```sh
svn info svn://server_path:3960/<repository_name>
```

**Ignore files and folders**

```sh
svn propset svn:ignore "*.tmp" .
svn propset svn:ignore dirname .
svn propedit svn:ignore . # To multiple things, open the default editor
```

# Configurations
To change the default editor for subversion, access the file ```~/.subversion/config``` in the section **[helpers]** and set the property **editor-cmd**:
```
[helpers]
editor-cmd = vim
```
