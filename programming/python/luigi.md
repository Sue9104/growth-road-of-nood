# Luigi

## Configuration

> [ht**t**ps://luigi.readthedocs.io/en/stable/configuration.html](https://luigi.readthedocs.io/en/stable/configuration.html)

Support parsers:  toml or cfg

Locations:&#x20;

* **/etc/luigi/luigi.cfg**
* **luigi.cfg**
* **LUIGI\_CONFIG\_PATH**

```
[core]
default_scheduler_url=http://localhost:8082/
log_level=DEBUG

[resources]
cpu=8
memory=16

[scheduler]
# Disable jobs that fail once
retry_count=1
disable_failures=1
disable-num-failures=1
# The disabled state persists for 1 second only
disable-persist-seconds=1
disable-window-seconds=1
# If a worker disconnects, remove all its jobs in 6 seconds
worker-disconnect-delay=6
# If a task has no stakeholders, remove it in 10 seconds
remove_delay=10

[worker]
keep_alive=True
wait_jitter=0
wait_interval=1
```

## Task

### tracking

* self.set\_progress\_percentage()
*   self.set\_status\_message()

    ```
    self.set_status_message(
    ```

    ```
    self.set_progress_percentage(i)
    ```

