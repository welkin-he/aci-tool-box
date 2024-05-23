# ACI Log Savor 

This script regularly pull off ACI switch's in-memory logs and archived logs, to prevent them being rolled over.
And offer option to generate ACI techsupport when required.


# Required python3 and below packages

urllib3
requests
ubuntu 20


## Full Run Example

<pre>

admin@ubuntu:~/demo$ python3 logsavor -s -i 192.168.20.40
Username: admin
PassWord:
PDT 2023-04-10T23:18:52.855||INFO||(142)||Build Fabric List
PDT 2023-04-10T23:18:52.929||WARNING||(154)||Skip: Node 202 OOB mgmt address is not configured
PDT 2023-04-10T23:18:53.007||INFO||(637)||Add the ssh-pub key below to user admin on 192.168.20.40
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCijsbJafM96WwvC9Sn/K0R2jAndTkkYAupH1OCtE5CQtcNi9V9Dt7FpfVk5+f1i7PgAAOve9MxBbgFBLq6Ed+pHQ2qTpzn8eRoTWffxUkrUGJXQcdOywqWOMkxRcmTrRhFttEQJTqn4SRm5ITlmhkgjeDBuCgQ4Cj5RZI5lUXicjbFO2v6ykiGzbcueNlU+hbcBxsb0LctzpiFvUHNeTbgKOfDulJZBrwRRPf8DrocBh1te0B2h1xU8amvku6qyB1UoMGuwssQrKCIap28KNVkJhZCFQJlciJQt0/Q5pPghrcC5NJdKv5aDGp2QXRq8Bz44qzrlAdPnt+oX9vUrHrH tianhe@aci-logviewer

PDT 2023-04-10T23:18:53.008||INFO||(641)||
Usage with OOB: nohup python3 logsavor -f FabricA -u admin &
Usage with INB: nohup python3 logsavor -f FabricA -u admin -c inb &


admin@ubuntu:~/demo$ nohup python3 logsavor -f FabricA -u admin &
[1] 42670
admin@ubuntu:~/demo$ nohup: ignoring input and appending output to 'nohup.out'

admin@ubuntu:~/demo$ nohup  python3 logsavor -f FabricA -u admin -n 101,102 &

admin@ubuntu:~/demo$ cat nohup.out

PST 2024-01-17T18:19:24.728||INFO||(186)||loading json file: FabricA/fabric_node.json
PST 2024-01-17T18:19:24.728||INFO||(194)||21 records loaded from FabricA/fabric_node.json
PST 2024-01-17T18:19:24.729||INFO||(740)||Regular log saving timer started for node 101
PST 2024-01-17T18:19:24.730||INFO||(740)||Regular log saving timer started for node 102
PST 2024-01-17T18:21:24.729||INFO||(363)||Fabric: FabricA, Node: 101, Current Version: 15.2-5c, Syncing remote directory: /var/sysmgr/tmp_logs/
PST 2024-01-17T18:21:24.732||INFO||(363)||Fabric: FabricA, Node: 102, Current Version: 15.2-5c, Syncing remote directory: /var/sysmgr/tmp_logs/
PST 2024-01-17T18:22:55.231||INFO||(417)||Fabric: FabricA, Node: 102, Current Version: 15.2-5c, /var/sysmgr/tmp_logs/ is synced between active and archive
PST 2024-01-17T18:23:00.129||INFO||(417)||Fabric: FabricA, Node: 101, Current Version: 15.2-5c, /var/sysmgr/tmp_logs/ is synced between active and archive



admin@ubuntu:~/demo$ python3 logsavor -f  FabricA -n 101 -t
PDT 2023-04-17T01:26:34.775||INFO||(185)||loading json file: CAP1/fabric_node.json
PDT 2023-04-17T01:26:34.790||INFO||(193)||18 records loaded from CAP1/fabric_node.json
PDT 2023-04-17T01:26:34.790||INFO||(697)||Tech-support for node 101 should start within 30 seconds
