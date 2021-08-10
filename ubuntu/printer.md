# Printer

## Background 

Ubuntu uses the Common UNIX Printing System \("CUPS"\) to handle printing. **CUPS uses the Internet Printing Protocol \("IPP"\) as the basis for managing print jobs and queues.** Other protocols are also supported \(LPD, SMB, AppSocket a.k.a JetDirect\), some with reduced functionality.

## Print

```text
lpr -P 322-printer -o media=a4 -o sides=one-sided *pdf
```

## Queque

```text
lpq -P 322-printer
```

{% hint style="danger" %}
when printer is not ready

**`cupsenable 322-printer`**
{% endhint %}

## Information

```text
#show models
lpinfo -m

#show devices
lpinfo -v
```

## Administration

```text
lpadmin -p 322-printer -o printer-error-policy=retry-current-job
```



