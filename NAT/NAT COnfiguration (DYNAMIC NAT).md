
set ip in all router
set ip nat in/out-side
set route rip
set NAT

! NAT: dynamic pool (no overload -> dynamic NAT)
ip nat pool todd-nat 170.168.1.10 170.168.1.20 netmask 255.255.255.0

! ACL matching both inside subnets
access-list 1 permit 192.168.1.0 0.0.0.255
access-list 1 permit 192.168.2.0 0.0.0.255

! Bind ACL to pool -> dynamic NAT (no PAT)
ip nat inside source list 1 pool todd-nat