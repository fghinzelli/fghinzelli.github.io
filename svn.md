# Server commands
## Create a new repository
```svnadmin create <repository_name>```

# Client commands

**Repository info**

```sh
svn info svn://server_path:3960/<repository_name>
```

**Revert changes**

```sh
svn revert <path_or_file>
```

**Remove files from version control**

```sh
svn delete <path_or_file> # remove the file from the directory local
svn delete --keep-local <path_or_file> # keep the file unversioned in local directory
```

**Ignore files and folders**

```sh
# Ignore valid only to children files and folders
svn propset svn:ignore "*.tmp" .
svn propset svn:ignore dirname .
svn propedit svn:ignore . # To multiple things, open the default editor

# Ignore hieritable for all children
svn propset svn:global-ignores ".git" .
svn propedit svn:global-ignores . # To multiple things, open the default editor

# Show all files ignored
svn status --no-ignore | grep "^I"
```

**Commit changes**
```sh
# Add files
svn add <files_or_path_or_pattern>
svn commit -m "Message"
```

# Configurations
To change the default editor for subversion, access the file ```~/.subversion/config``` in the section **[helpers]** and set the property **editor-cmd**:
```
[helpers]
editor-cmd = vim
```
