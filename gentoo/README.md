This part of the project is for Gentoo Linux.
The entire project has been restructured with
Gentoo in mind. The folder structure here
is the expected folders they will run from
out of root (/).

Either copy the files yourself, or you can
add the https://github.com/dl200010/dl-overlay
portage overlay and emerge it, but portage
will not install the /etc/openvpn/* files. Those
will have to be manually setup as part of
the openVPN install with your connection files.
Modify /etc/vpnfirewall/config to point to your
openvpn.conf file and your local IPv4 network.

This part of the firewall will be maintained here by dl200010:
https://github.com/dl200010/vpn-firewall/
