sgw
===
tungstenfabric demo bgp gateway with GoBGP controlplane and linux kernel dataplane

install
=======
Should work on any Linux system. You may need recent kernel for udp tunneling support.

    curl -O https://raw.githubusercontent.com/YKonovalov/sgw/master/sgw
    sudo ./sgw --install

configuring
===========
Config file is /etc/sgw/init.rc . Print example and create your own config file:

    sgw --config-example


use
===
Setup controlplane and dataplane

    sgw --create

show status

    sgw -s

show routes

    sgw -l

show menu of scopes and available actions

    sgw

uninstall
=========

    sgw --delete


limits
======

1. VRF:
  - Maxumum number of VRF interfaces are infinite (memory is the only limit) - stored as linked list in the kernel.
  - Maximum number of routing tables is defined in kernel RT_TABLE_MAX is 0xFFFFFFFF (2^32-1) = 4294967295.
2. Route:
  - Maximum number of routes is not fixed in the kernel - stored as linked list. Practically memory is the limit.
3. TC Flower filter:
  - ? Maximun number of tc flower filters is probably unlimited and depens only on available memory
4. Hardware offload:
  - Flows - ?
  - Encapsulations - ?
  - Routes - ?
