# rsyslog

/etc/rsyslog.conf
/etc/rsyslog.d./*.conf

```
     FILTER                PATH
/---------------\   SYNC
FACILITY.PRIORITY    (-)/var/log/logfile
```

### Facility
|name|num|
|-------|-:|
|kern    |0|
|user    |1|
|mail    |2|
|daemon  |3|
|auth    |4|
|syslog  |5|
|lpr     |6|
|news    |7|
|uucp    |8|
|cron    |9|
|authpriv|10|
|ftp     |11|
|local0-local7|16 - 23|

### Priority
|name  |num|
|-------|-:|
|debug   |7|
|info    |6|
|notice  |5|
|warning |4|
|err     |3|
|crit    |2|
|alert   |1|
|emerg   |0|

|Code|Priority| Severity
|0   |emerg   | System is unusable.
|1   |alert   | Action must be taken immediately.
|2   |crit    | Critical condition.
|3   |err     | Non-critical error condition.
|4   |warning | Warning condition.
|5   |notice  | Normal but significant event.
|6   |info    | Informational event.
|7   |debug   | Debugging-level message.
