## Set interfaces
*When setting interfaces be sure to add the interface to the virtial router before committing.*

``` 
set network interface ethernet ethernet1/1 layer3 dhcp-clent enable yes create-default-route yes
set network virtual-router default interface ethernet1/1 
```
To confirm the config `show network interface`
```
show network interface 
interface {
  ethernet {
    ethernet1/1 {
      layer3 {
        dhcp-client {
          enable yes;
          create-default-route yes;
        }
      }
    }
  }
}
```
To confirm the interface is pulling an IP via DCHP `show interface all` to see all interface properties. Or run `show interface ethernet1/1 | match 'Interface IP address'` to show only the IP address information.
```
show interface ethernet1/1 | match 'Interface IP address'
Interface IP address (dynamic): 192.168.100.186/24
```
## Set security zone
```
set zone untrust network layer3 ethernet1/1
```
  
## Set security rule
*Use of any/any/any rule is not advisable. For lab use only!*
```
set rulebase security rules trust-to-untrust from trust to untrust source any destintion any action allow service any application any
```
To see security rules you have to be in config mode
`show rulebase security rules`
```
show rulebase security rules 
rules {
  trust-to-untrust {
    from trust;
    to untrust;
    source any;
    destination any;
    action allow;
    service any;
    application any;
  }
}
```
