sgw
===
tungsten bgp gateway with GoBGP controlplane and linux kernel dataplane demo

install
=======
Known to work on Centos 8 and Fedora 32, but other distros should be ok too. You may need recent distro for udp tunneling support in the kernel.

    sudo install -m 700 sgw /usr/local/bin/

configuring
===========
There is no configuration file. Look at the top of the script and tune vrfs and bgp peer vars. You may also set your bgp peer in file:

    echo "192.168.0.2" > /root/bgpneigh

There is no support for udp tunneling in stock CentOS 8 kernel, so disable it:

    touch /root/noudp

If you want static tunnels to be configured instead of lightweight route-based tunnels:

    touch /root/nolwtun

use
===
Setup controlplane and dataplane (known to work on Centos 8 and Fedora 32, but other distros should be ok too)

    sgw --create # or --delete to revert changes

show status

    sgw -s

show routes

    sgw -l

show menu of scopes and available actions

    sgw
