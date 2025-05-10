This part of the project is for Gentoo Linux.
The entire project has been restructured with
Gentoo in mind. The folder structure here
is the expected folders they will run from
out of root (/).

Either copy the files your self, your you can
add the https://github.com/dl200010/dl-overlay
portage overlay and emerge it, but the ebuild
does not install the openvpn/* files. Those
will have to be manually setup as part of
the openVPN install with your connection files.

This part of the firewall will be maintained here by dl200010:
https://github.com/dl200010/vpn-firewall/
