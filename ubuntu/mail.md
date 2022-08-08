# Mail

## SSMTP

### Install

```text
sudo apt install ssmtp
```

### Configure

```text
# add in /etc/ssmtp/ssmtp.conf
root=sumin2012@163.com
mailhub=smtp.163.com:465
rewriteDomain=163.com
AuthUser=sumin2012
AuthPass=Sum.0608
FromLineOverride=YES
UseTLS=YES


# add in /etc/ssmtp/revaliases
minsu:sumin2012@163.com:smtp.163.com:465
```

### Send

```text
echo "Test" | mail -s "subject_title" receipt@mail.com

mail -s "subject_title" receipt@mail.com < file
```

