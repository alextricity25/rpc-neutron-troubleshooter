# rpc-neutron-troubleshooter
There are many reasons why neutron might not be working on an RPC cluster. This script provides some tools to help set-up and troubleshoot neutron in RPC.

## Creating the essential neutron networking components 
This script has the ability to create all the essential networking components for a fully functional neutron (Assuming the physical plumbing is already in place). This script will create a physical provider network and subnet according what the global constants are set to in the beggining of the script. It will then create a tenant network and subnet on the 10.10.10.0/24 network. The tenant networks will use the vxlan tunneling protocol implementation. Routers will be created with the physical provider network set to the gateway, and the tenant network set as a router interface.

###Usage
./manageNeutron.py --source_file \<path\> create --all
