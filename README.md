# Manage ldap users via ansible

## Description

This utility will allow you to manage ldap users.
You can create either posix user for use on linux hosts or organizationalPerson for use for company employees.

## Requirements

ansible 2.4.0.0

## Installation

git clone or download file(s) to your host

## Configuration

edit vars/secure.yml
```
server_uri: ldap://mydomain.net
bind_dn: cn=admin,dc=mydomain,dc=net
bind_pw: mypassword
```
edit vars/ldap.yml
```
ldap_base: ou=People,dc=mydomain,dc=net
ldap_group: ou=Group,dc=mydomain,dc=net
```


## posix

```
# add
ansible-playbook create_ldap_user.yml -e user=aauser -e type=posix

# edit
ansible-playbook create_ldap_user.yml -e user=aauser -e type=posix --tags edit   -e force=true

# remove
ansible-playbook create_ldap_user.yml -e user=aauser -e type=posix --tags remove -e force=true
```

muliple users
```
# add
ansible-playbook create_ldap_user.yml -e user=aauser,aauser1 -e type=posix

# edit
ansible-playbook create_ldap_user.yml -e user=aauser,aauser1 -e type=posix --tags edit   -e force=true

# remove
ansible-playbook create_ldap_user.yml -e user=aauser,aauser1 -e type=posix --tags remove -e force=true
```

## organizationalPerson

single user only
```
# add
ansible-playbook create_ldap_user.yml -e user=aauser -e type=user  -e firstname=first -e lastname=lastname -e title=title -e mobile=mobile -vvv

# edit
ansible-playbook create_ldap_user.yml -e user=aauser -e type=user  -e firstname=first -e lastname=lastname -e title=title -e mobile=mobile -vvv  --tags edit   -e force=true

# remove
ansible-playbook create_ldap_user.yml -e user=aauser -e type=user  -e firstname=first -e lastname=lastname -e title=title -e mobile=mobile -vvv  --tags remove -e force=true
```
