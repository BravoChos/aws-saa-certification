**Section: VPN Connections**
You can create an IPsec VPN connection between your VPC and your remote network. On the AWS side of the VPN connection, a virtual private gateway **provides two VPN endpoints** (tunnels) for automatic failover. You configure your customer gateway on the remote side of the VPN connection.

AWS recommends that you use **BGP-capable** VPN devices when available, because the BGP protocol offers **robust liveness detection checks** that can assist failover to the second VPN tunnel if the first tunnel goes down. Devices that don't support BGP may also perform health checks to assist failover to the second tunnel when needed.

A VPN connection has two tunnels to help ensure connectivity in case one of the VPN connections becomes unavailable. To protect against a loss of connectivity in case your customer gateway becomes unavailable, you can set up a second VPN connection to your VPC by using a second customer gateway.






