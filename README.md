Avoid corruption on the Juniper VMrouter

Run this on first shutdown.

root@vmrouter-1> request system halt 

Then shut down on EVE-NG Topology

Troubleshooting Juniper MPLS and IS-IS.

Check ISIS

root@vmrouter-1> show isis adjacency 

Interface             System         L State         Hold (secs) SNPA
ge-0/0/0.0            router-2       2  Up                    20  50:1:0:2:0:4

Check MPLS interface assigned

root@vmrouter-1> show mpls interface 
Interface        State       Administrative groups (x: extended)
ge-0/0/0.0       Up         <none>

Check connected MPLS LDP routers

root@vmrouter-1> show ldp neighbor 
Address                             Interface       Label space ID     Hold time
10.20.0.2                           ge-0/0/0.0      172.16.2.1:0         12

show routing table on the device
root@vmrouter-1> show route 

inet.0: 31 destinations, 31 routes (31 active, 0 holddown, 0 hidden)
+ = Active Route, - = Last Active, * = Both

10.0.0.0/30        *[IS-IS/18] 00:06:40, metric 30
                    >  to 10.20.0.2 via ge-0/0/0.0
10.1.0.0/30        *[IS-IS/18] 00:06:44, metric 20
                    >  to 10.20.0.2 via ge-0/0/0.0
<--- Compressed ---->

