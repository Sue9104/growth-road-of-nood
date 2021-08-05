# Samba

## Setup

* install sambda

```text
sudo apt-get install samba smbfs
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
```

* create the share folder and change permissions

```text
sudo mkdir /your-share-folder
sudo chmod 777 -R /your-share-folder
```

## Connect share folder on Ubuntu

Ctrl + L 打开地址栏，输入share folder: **`smb://ip/your-share-folder`**

## Download file from share folder

```text
smbget -R smb://user:passwd@ip/your-share-folder/
```

## Upload file to share folder

```text
# one file
curl --upload-file your-local-file smb://user:passwd@ip/your-share-folder

# folder
smbclient //ip/your-share-folder -U user --pass passwd -c 'prompt OFF; recurse ON; cd your-share-path; lcd your-local-path; mput *'
```

## 

