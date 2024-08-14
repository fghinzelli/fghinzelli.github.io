https://medium.com/@amrutha_20595/setting-up-openldap-server-with-docker-d38781c259b2
```bash
# Search basic
ldapsearch -x -H ldap://localhost:1389 -b dc=example,dc=org

# Create User accounts.
ldapadd -x -H ldap://localhost:1389 -W -D "cn=admin,dc=example,dc=org" << EOF
# LDIF file to Create user "alguem" in "ou=users" under "dc=example,dc=org"
dn: cn=alguem,ou=users,dc=example,dc=org
objectClass: person
cn: alguem
sn: Alguem
userPassword: alguem123
EOF
```
