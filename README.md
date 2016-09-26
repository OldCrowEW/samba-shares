# samba-shares
Simple vagrant file using ansible to provision samba proof of concept.

## Add samba user / password
```
smbpasswd -a {{ user }}
```