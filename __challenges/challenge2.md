**Create config map**

1. name: time-config
2. with data: TIME_FREQ=10

**Create pod**

1. name: time-check
2. Mount path: /opt/time on empty dir
3. Run command: while true; do date; sleep $TIME_FREQ; done
4. Write result of the command to: /opt/time/time-check.log
