# Linux

## grep commands
``` 
# List text without comments (#)
grep -v '^#' file1 file2 file3 
```

## Add a program to default path
```bash
# Create a symbolic link in /usr/local/lib
ln -s /opt/program/program.sh /usr/local/lib
``` 

## Change permissions
```bash
chomod u+r | chmod g+r | chmod o+r | chmod ugo+r
```

## Find patterns
```bash
grep "<pattern>" <filename>  
<command_output> | grep "pattern"
```
## Find process ID
```bash
ps -A | pgrep code
```

## Disk space
```df
du -sh <directory_name> # Espaço de uma pasta
```

## Convert to base64
``` echo -n 'user:pwd' | base64 ```


# Log in bash   
``` 
#!/bin/bash
# redirect stdout/stderr to a file
exec &> logfile.txt 
```

## DNS

- Clear DNS
``` sudo systemd-resolve --flush-caches ```

## SSH 

- Generate Keys (~/.ssh/id_rsa)
``` ssh-keygen ```

- Copy public keys to server
``` ssh-copy-id -i ~/.ssh/id_rsa.pub username@servername ```

## Create a new Item in the laucher menu
```
# create a new file in /usr/share/applications and save with this informations
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=<Sample Application Name>
Comment=<A sample application>
Exec=/opt/<application>
Icon=<application.png>
Terminal=false
Categories=Application
```

## CentOS on Docker - Executar yum update
```
sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
```

## VNC
[https://www.server-world.info/en/note?os=Ubuntu_19.04&p=desktop&f=5](https://www.server-world.info/en/note?os=Ubuntu_19.04&p=desktop&f=5)
[https://www.tecmint.com/install-and-configure-vnc-server-on-ubuntu/](https://www.tecmint.com/install-and-configure-vnc-server-on-ubuntu/)

## Links
[Bash academy](https://www.bash.academy/)  
[Bash Begginners Guide](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/)  
[Bash Prog](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)  
[Regex](https://regexr.com/)  

