# streaming replication

each change is sent to one or more replica servers directly over a TCP/IP connection as it happens. The replicas must have a direct network connection the master configured in their recovery.conf's primary\_conninfo option.

## 区别

> [https://stackoverflow.com/questions/33621906/difference-between-stream-replication-and-logical-replication](https://stackoverflow.com/questions/33621906/difference-between-stream-replication-and-logical-replication)

* WAL-shipping vs streaming
* Asynchronous vs synchronous streaming
* Logical vs physical

