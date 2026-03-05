# Why
If you simply add a VPN using common instructions, it generally fails open. That means, if the VPN breaks down, because the connection is interrupted, traffic will be send without the VPN.

It's much safer when it fails closed, i.e. when the VPN connection breaks down, the whole internet connection must be down as long as the VPN connection isn't restored.

# What does it do

* Forbid outgoing traffic after the VPN / tunnel software broke down for some reason.
* Tight firewall rules, using iptables policy drop.
* Only designed with OpenVPN in mind.
* You should test if it does what it claims.
* Open Source / Free Software

# What does it NOT do

* Care about DNS leaks. Consult your VPN software's/provider's documentation and
configure /etc/resolv.conf to use the DNS server of your VPN server.
* Block WebRTC leaks. [1]
* Defend against
[IP leaks](https://blog.torproject.org/blog/bittorrent-over-tor-isnt-good-idea).
If a locally installed application uses trickery to obtain the the users real
IP and sends it somewhere though the VPN. [1]
* Defend against adversaries, which are in position to run code locally, i.e.
manipulate the firewall rules.
* Prevent any other kind trickery to circumvent using the VPN.
* Prevent leaks caused by bugs in the VPN software.
* Be compatible with Whonix-Gateway/Workstation. (VPN-Firewall is incompatible with Whonix-Gateway/Workstation's firewall! Use Whonix documentation and use their built-in features.)
* Manage IPv6 traffic. IPv6 traffic is blocked.
* Install (Open)VPN.
* Configure (Open)VPN.
* Autostart (Open)VPN.
* Anything else not mentioned above in "What does it do".

[1] This probably does not apply to VMs / computers behind a VPN-Gateway (when using the #Forwarding feature).

# Dependencies

* sys-libs/glibc
* sys-apps/coreutils
* sys-apps/grep
* sys-apps/sed
* sys-apps/gawk
* sys-apps/iproute2
* net-firewall/iptables
  * https://wiki.gentoo.org/wiki/Iptables
  * Kernel 6.17+
    * The kernel needs "CONFIG_NETFILTER_XTABLES_LEGACY" / "Netfilter legacy tables support" turned on.
    * I will work on moving over to nftables, eventually.
    * https://www.kernelconfig.io/config_netfilter_xtables_legacy
* net-vpn/openvpn
* Kernel compiled with

# How to Use

* Emerge the dependencies above.
* Install the files in the gentoo folder by
  * Coping the files, or
  * Use the https://github.com/dl200010/dl-overlay portage overlay and "emerge net-vpn/vpn-firewall".
    * This will install the dependencies above.
* Edit /etc/vpnfirewall/config to point to your openvpn.conf file and openvpn interface.
* Edit /etc/init.d/openvpn to add "need vpnfirewall" to the end of "depend()".
* Use "/etc/init.d/vpnfirewall start" to start right away.
* Use "rc-update add vpnfirewall default" to auto start when booting up.

# Forks, Patches, Testers, Comments, etc.

Welcome.

# Original Author

* Patrick Schleizer
* e-mail: adrelanos@riseup.net
* [gpg](https://www.whonix.org/wiki/Patrick_Schleizer): 916B8D99C38EAF5E8ADC7A2A8D66066A2EEACCDA
* twitter: https://twitter.com/Whonix
* [Donate](https://www.whonix.org/wiki/Donate)

# Gentoo Author

* Chris Dangerfield
* e-mail: dl200010@gmail.com

# License

GPLv3+
