# Server commands
**Default path of repositories**
```/var/lib/svn```

**Create a new repository**
```svnadmin create <repository_name>```

**Edit permissions**
 Edit de files in the folder <directory>/conf (authz, passwd, perms, svnserve.conf)

# Client commands

**Repository info**

```sh
svn info svn://server_path:3960/<repository_name>
```

```sh
svn info
# Returns the info about the current path on svn
```

**Revert changes**

```sh
svn revert <path_or_file>
```

**Add files**
```sh
svn add <file/directory> # Add new file/directory
svn status | grep '^?' | awk '{print $2}' | xargs svn add # Add all new files
```

**Remove files from version control**

```sh
svn delete <path_or_file> # remove the file from the directory local
svn delete --keep-local <path_or_file> # keep the file unversioned in local directory
svn status | grep '^!' | awk '{print $2}' | xargs svn delete # remove all files missing (deleted/renamed)

# Remove files from server
svn delete svn://<svn_server>/<repo>/<path_to_delete> -m "Message to commit"
``` 
**Ignore files and folders**

IMPORTANT: The propset is related to the current folder. Not include paths, to subfolders

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

# Branching
http://svnbook.red-bean.com/en/1.7/svn.branchmerge.basicmerging.html#svn.branchemerge.basicmerging.reintegrate

**Create new brach**
```
svn copy svn://<server>/<repository>/trunk svn://<server>/<repository>/branches/<new_branch>
```
**Merge with trunk (To keep feature branch updated)**
svn merge svn://<server>/<repository>/branches/<branch_name> svn://<server>/<repository>/trunk

**Integration with trunk (To publish the feature branch on production branch)**
# Go to trunk workin copy
svn checkout svn://<server>/<repository>/trunk
# Update the working copy
svn update
# Get changes from your feature branch
svn merge svn://<server>/<repository>/trunk svn://<server>/<repository>/branches/<branch_name>

# Configurations
To change the default editor for subversion, access the file ```~/.subversion/config``` in the section **[helpers]** and set the property **editor-cmd**:
```
[helpers]
editor-cmd = vim
```
# Articles
https://dev.to/rajbdilip/quick-svn-guide-for-git-users-svn-the-git-way-26al

