# Install OpenVPN #


## Introduction ##

This role will install and set up OpenVPN server on Ubuntu and RedHat-family OS. Tested on Ubuntu 14.04/16.04, CentOS 6/7.

It configure OpenVPN for set up VPN in NAT access mode, meaning user is not visible from the OpenVPN server's network, and all traffic from user is seen
as from OpenVPN server itself.

This role does not generate users, but it contains scripts that manage users, so that the openvpn-user role can be used to create VPN users. The reason for
this separation is that openvpn-user can be run from other machine, as another user that the ones that install openvpn, without the later's privileges.


## Variables ##

Variables used in Easy-RSA vars file: 
  - openvpn_key_size : (default 1024)
  - openvpn_ca_expire : (default 3650)
  - openvpn_key_expire : (default 3650) 
  - openvpn_key_name : (default "vpnserver") 
  - openvpn_key_country : (default "US") 
  - openvpn_key_province : (default "CA") 
  - openvpn_key_city : (default "SanFrancisco") 
  - openvpn_key_org : (default "Fort-Funston") 
  - openvpn_key_email : (default "me@myhost.mydomain") 
  - openvpn_key_ou : (default "MyOrganizationalUnit") 

Variables used in OpenVPN server.conf:

  - openvpn_port : (default 1194) OpenVPN port
  - openvpn_use_tls : (default True)  : if True, will generate and use TLS
  - openvpn_protocol : (default udp) : udp or tcp as VPN transport.
  - openvpn_duplicate_cn : (default True) : Let one client key be used by multiple sessions in the same time
  - openvpn_vpn_subnet : (default "10.8.0.0/24") : Subnet for VPN tunnel. MUST be different from client's or server's network sides.
  - openvpn_push_route : (default []) : route to push to client. Normally it contains at least contains server's private network.


Other variables:
  - openvpn_force_restart : (default False) If True, will force restarting OpenVPN. It is useful in maintenance operations.

## Notes on this playbook ##
  - RedHat OS must have access to OpenVPN package, such as EPEL repository.


## Credit ##

This playbook get influence from the work of [Stous](https://github.com/Stouts/Stouts.openvpn)
