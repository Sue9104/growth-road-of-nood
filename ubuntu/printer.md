# Printer

## Background&#x20;

Ubuntu uses the Common UNIX Printing System ("CUPS") to handle printing. **CUPS uses the Internet Printing Protocol ("IPP") as the basis for managing print jobs and queues. **Other protocols are also supported (LPD, SMB, AppSocket a.k.a JetDirect), some with reduced functionality.

## Setup

```
sudo apt install cups
sudo systemctl start cups
systemctl status cups
```

> [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
>
> [https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint](https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint)

### options

```
# list printer detail
lpoptions -p szyc-322 -l
# set printer default setting
lpoptions -p szyc-322 -o PageSize=A4 -o Duplex=None
```

## Print

```
lpr -P 322-printer -o media=a4 -o sides=one-sided *pdf
```

## Queque

```
lpq -P 322-printer
```

{% hint style="danger" %}
when printer is not ready

**`cupsenable 322-printer`**
{% endhint %}

## Information

```
#show models
lpinfo -m

#show devices
lpinfo -v
```

## Administration

```
lpadmin -p 322-printer -o printer-error-policy=retry-current-job
```

