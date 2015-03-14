## Netout

Netout pings a host and logs outages to a file.

Use netout to ping 8.8.8.8:
```
netout 
```

That logs any problems pinging 8.8.8.8 (google-public-dns-a.google.com) to `outages_8.8.8.8.txt`, e.g.:
```
Outage started 2015-03-13 22:05:56 -0400 (No route to host) and ended 2015-03-13 22:06:06 -0400
Outage started 2015-03-13 22:06:12 -0400 (No route to host) and ended 2015-03-13 22:06:16 -0400
Outage started 2015-03-13 22:06:32 -0400 (No route to host) and ended 2015-03-13 22:06:36 -0400
```

In a separate shell session, you can `tail -f` the file to get output.

Use netout to ping 1.2.3.4 and logs any problems pinging 1.2.3.4 (google-public-dns-a.google.com) to `outages_1.2.3.4.txt`:
```
netout 1.2.3.4
```

### How to use

Ensure that [Ruby](https://www.ruby-lang.org) is installed/available and then put the netout script somewhere in your path.

### How it works

Netout is a Ruby script that uses popen to call `ping -t500 ('8.8.8.8' or provided args) 2>&1` and watches the stdout and stderr streams. If it notices an outage start or recovery it logs those immediately to a file.

### License

Copyright (c) 2015, Gary S. Weaver, released under the [GNU General Public License version 3](gpl.txt) as published by the Free Software Foundation.