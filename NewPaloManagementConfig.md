## How to setup a new Palo Alto Firewall
*This document provide minimum information for setting up connectivity to manage the firewall.*

Boot up device and connect console cable. Default username and password is `admin`.
### Change admin password:
```
configure
set mgt-config users admin password <Press ENTER>
Enter password: ******
Confirm password: ******
commit
```
Enter password manually to confirm.

### Update management interface
The Palo Alto default management IP is 192.168.1.1 at device boot. If using a VM the managemnt IP most likely will be blank. Use this IP if connecting on a local network to manage via CLI or GUI. If this subnet is not available on your network then set manually as noted below:
```
configure
set deviceconfig system ip-address <Static IP> netmask <Netmask> default-gateway <Gateway IP> type static
commit
```
Log into GUI by using the IP address in your browser.
