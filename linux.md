# Linux

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

## VNC
[https://www.server-world.info/en/note?os=Ubuntu_19.04&p=desktop&f=5](https://www.server-world.info/en/note?os=Ubuntu_19.04&p=desktop&f=5)
[https://www.tecmint.com/install-and-configure-vnc-server-on-ubuntu/](https://www.tecmint.com/install-and-configure-vnc-server-on-ubuntu/)

## Links
[Bash academy](https://www.bash.academy/)  
[Bash Begginners Guide](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/)  
[Bash Prog](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)  
[Regex](https://regexr.com/)  

