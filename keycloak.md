#Keyckoak


### Custom themes
https://www.baeldung.com/spring-keycloak-custom-themes

### Custom attributes
https://www.baeldung.com/keycloak-user-registration


### Docker

https://hub.docker.com/r/jboss/keycloak/dockerfile

- To Install packages in ubi8minimal image:
```
 microdnf update
 microdnf install <package>
```
  
https://developers.redhat.com/blog/2019/05/31/working-with-red-hat-enterprise-linux-universal-base-images-ubi/


## Run standalone  (To run in 8088 port)
```./bin/standalone.sh -b 0.0.0.0 -Djboss.socket.binding.port-offset=8 &```     
If is set in the config file (standalone.xml)
```./bin/standalone.sh -b 0.0.0.0 &```
