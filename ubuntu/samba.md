# Samba

## Setting

* install sambda

```text
sudo apt-get install samba smbfs smbclient
```

* configure

```text
vi /etc/samba/smb.conf
```

* set workgroup if necesary
* set share folders

```text
[MyShare]
  comment = YOUR COMMENTS
  path = /your-share-folder
  read only = no
  guest ok = yes
```

* restart samba

```text
/etc/init.d/samba restart
# sudo service smbd restart
```

* create the share folder and change permissions

```text
sudo mkdir /your-share-folder
sudo chmod 777 -R /your-share-folder
```

## Connection

* Ctrl + L 打开地址栏，输入share folder: 

```text
smb://ip/your-share-folder
```

* mount cifs

```text
sudo mount -t cifs -o username=username,password=passwd //ip/folder/ /mnt/yck
```

{% hint style="danger" %}
mount error\(13\): Permission denied

check setting in "/etc/samba/smb.conf"

* browseable
* hosts allow
* valid users
{% endhint %}

## Download

```text
smbget -R smb://user:passwd@ip/your-share-folder/
```

## Upload

```text
# one file
curl --upload-file your-local-file smb://user:passwd@ip/your-share-folder

# folder
smbclient //ip/your-share-folder -U user --pass passwd -c 'prompt OFF; recurse ON; cd your-share-path; lcd your-local-path; mput *'
```

## 

