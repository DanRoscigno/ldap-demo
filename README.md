# ldap-demo

```
gcloud container clusters get-credentials ee-docs --region us-central1 --project enterprise-demo-422514
```

```
kubectl get pods -n openldap-demo
```

```
kubectl get services -n openldap-demo
```

```
NAME           TYPE           CLUSTER-IP       EXTERNAL-IP     PORT(S)         AGE
ldap-service   LoadBalancer   34.118.225.124   34.30.114.160   389:32363/TCP   5m17s
```

```
10109  ldapsearch -x -b dc=example,dc=org -D "cn=admin,dc=example,dc=org" -w admin -H ldap://34.30.114.160 -L
```

```
version: 1

#
# LDAPv3
# base <dc=example,dc=org> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# example.org
dn: dc=example,dc=org
objectClass: top
objectClass: dcObject
objectClass: organization
o: Example Inc.
dc: example

# People, example.org
dn: ou=People,dc=example,dc=org
objectClass: organizationalUnit
ou: People

# jane, People, example.org
dn: cn=jane,ou=People,dc=example,dc=org
objectClass: person
objectClass: inetOrgPerson
sn: doe
cn: jane
mail: janedoe@example.com
userPassword:: Zm9v

# john, People, example.org
dn: cn=john,ou=People,dc=example,dc=org
objectClass: person
objectClass: inetOrgPerson
sn: doe
cn: john
mail: johndoe@example.com
userPassword:: YmFy

# sr_fte, People, example.org
dn: uid=sr_fte,ou=People,dc=example,dc=org
objectClass: inetOrgPerson
cn: sr_fte
uid: sr_fte
sn: FTE
givenName: SR
userPassword:: YmFy

# sr_contractors, People, example.org
dn: uid=sr_contractors,ou=People,dc=example,dc=org
objectClass: inetOrgPerson
cn: sr_contractors
uid: sr_contractors
sn: Contractors
givenName: SR
userPassword:: YmFy

# Groups, example.org
dn: ou=Groups,dc=example,dc=org
objectClass: organizationalUnit
ou: Groups

# admins, Groups, example.org
dn: cn=admins,ou=Groups,dc=example,dc=org
objectClass: groupOfNames
cn: admins
member: cn=john,ou=People,dc=example,dc=org
member: cn=jane,ou=People,dc=example,dc=org

# developers, Groups, example.org
dn: cn=developers,ou=Groups,dc=example,dc=org
objectClass: groupOfNames
cn: developers
member: cn=jane,ou=People,dc=example,dc=org

# sr_admin, Groups, example.org
dn: cn=sr_admin,ou=Groups,dc=example,dc=org
objectClass: groupOfNames
cn: sr_admin
member: uid=sr_fte,ou=People,dc=example,dc=org
member: uid=sr_contractors,ou=People,dc=example,dc=org

# search result

# numResponses: 11
# numEntries: 10version: 1

#
# LDAPv3
# base <dc=example,dc=org> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# example.org
dn: dc=example,dc=org
objectClass: top
objectClass: dcObject
objectClass: organization
o: Example Inc.
dc: example

# People, example.org
dn: ou=People,dc=example,dc=org
objectClass: organizationalUnit
ou: People

# jane, People, example.org
dn: cn=jane,ou=People,dc=example,dc=org
objectClass: person
objectClass: inetOrgPerson
sn: doe
cn: jane
mail: janedoe@example.com
userPassword:: Zm9v

# john, People, example.org
dn: cn=john,ou=People,dc=example,dc=org
objectClass: person
objectClass: inetOrgPerson
sn: doe
cn: john
mail: johndoe@example.com
userPassword:: YmFy

# sr_fte, People, example.org
dn: uid=sr_fte,ou=People,dc=example,dc=org
objectClass: inetOrgPerson
cn: sr_fte
uid: sr_fte
sn: FTE
givenName: SR
userPassword:: YmFy

# sr_contractors, People, example.org
dn: uid=sr_contractors,ou=People,dc=example,dc=org
objectClass: inetOrgPerson
cn: sr_contractors
uid: sr_contractors
sn: Contractors
givenName: SR
userPassword:: YmFy

# Groups, example.org
dn: ou=Groups,dc=example,dc=org
objectClass: organizationalUnit
ou: Groups

# admins, Groups, example.org
dn: cn=admins,ou=Groups,dc=example,dc=org
objectClass: groupOfNames
cn: admins
member: cn=john,ou=People,dc=example,dc=org
member: cn=jane,ou=People,dc=example,dc=org

# developers, Groups, example.org
dn: cn=developers,ou=Groups,dc=example,dc=org
objectClass: groupOfNames
cn: developers
member: cn=jane,ou=People,dc=example,dc=org

# sr_admin, Groups, example.org
dn: cn=sr_admin,ou=Groups,dc=example,dc=org
objectClass: groupOfNames
cn: sr_admin
member: uid=sr_fte,ou=People,dc=example,dc=org
member: uid=sr_contractors,ou=People,dc=example,dc=org   #member: cn\3Djohn,ou
 =People,dc=example,dc=org   #member: cn\3Djane,ou=People,dc=example,dc=org

# search result

# numResponses: 11
# numEntries: 10
```
