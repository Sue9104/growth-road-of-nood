# Cron

Job Scheduler

## Configure

The first five columns: minute, hour, day, day of month, month, day of week

| Special Characters | Purpose                                                          |
| ------------------ | ---------------------------------------------------------------- |
| asterisk(\*)       | all                                                              |
| question(?)        | unspecified, as \* \* \* 10 ?: 10th day and unkonown week        |
| dash(-)            | a range of values                                                |
| comma(,)           | a list of values                                                 |
| slash(/)           | skip a given number                                              |
| L                  | Last is allowed for day of month and day of week                 |
| W                  | Weekday is allowed for day of month                              |
| pound(#)           | pound is allowed for day of week, such as 6#3 (the third Friday) |

```bash
#!/bin/bash
*/1 * * * * ls -al /home >> test.log 2>&1
```

{% hint style="info" %}
Percent converts to a newline in crontab files

* escape: \\%
* write command in shell scripts
{% endhint %}

## Usage

```bash
sudo service cron start
sudo service cron stop


# submit jobs
crontab cron-files
# delete jobs
crontab -r
# edit jobs
crontab -e
## always restart cron after editing
sudo service cron restart
```

## Debug

* environment path
* writable permission
* check log: "grep cron /var/log/syslog"
