# Mail

## SSMTP

### Install

```
sudo apt install mailutils ssmtp
```

### Configure

```
# add in /etc/ssmtp/ssmtp.conf
root=sumin2012@163.com
mailhub=smtp.163.com:465
rewriteDomain=163.com
AuthUser=mailuser
AuthPass=mailpasswd
FromLineOverride=YES
UseTLS=YES


# add in /etc/ssmtp/revaliases
minsu:sumin2012@163.com:smtp.163.com:465
```

### Send

```
echo "Test" | mail -s "subject_title" receipt@mail.com

mail -s "subject_title" receipt@mail.com < file
```
