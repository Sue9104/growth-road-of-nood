# Plot

## Layout

### patchwork

{% embed url="https://github.com/thomasp85/patchwork" %}

```
library(patchwork)
(p1 | p2 | p3) / p4
```

<figure><img src="../../.gitbook/assets/image (1) (2).png" alt=""><figcaption></figcaption></figure>

### par

{% embed url="https://www.datamentor.io/r-programming/subplot/" %}

```
par(mfrow=c(1,2))
par(mfcol = c(2, 2))

# more precise control
## make labels and margins smaller
par(cex=0.7, mai=c(0.1,0.1,0.2,0.1))
Temperature <- airquality$Temp

## define fig coordinates as c(x1, x2, y1, y2)
par(fig=c(0.1,0.7,0.3,0.9))
hist(Temperature)
par(fig=c(0.8,1,0,1), new=TRUE)
boxplot(Temperature)
par(fig=c(0.1,0.67,0.1,0.25), new=TRUE)
stripchart(Temperature, method="jitter")

```

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
