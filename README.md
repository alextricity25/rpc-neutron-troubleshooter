# rpc-neutron-troubleshooter
There are many reasons why neutron might not be working on an RPC cluster. This script provides some tools to help set-up and troubleshoot neutron in RPC.

## Creating the essential neutron networking components
This script has the ability to create all the essential networking components for a fully functional neutron (Assuming the physical plumbing is already in place). This script will create a physical provider network and subnet according what the global constants are set to in the beggining of the script. It will then create a tenant network and subnet on the 10.10.10.0/24 network. The tenant networks will use the vxlan tunneling protocol implementation. A router will be created with the physical provider network set to the gateway, and the tenant network set as a router interface.

###Usage
```bash
./manageNeutron.py --source_file \<path\> create --all
```

## Deleting all essential neutron networking commponents (CAUTION)
This script has the ability to delete all the essential networking components for a tenant on an openstack environment. The networking components will be deleted according to what the global constants are set to in the script. All nova instances, or associated ports, must be deleted before running this command.

###Usage
```bash
./manageNeutron.py --source_file \<path\> delete --all
```

## Restarting all the neutron services
This script can restart all of the neutron services within an RPC environment, including the services running on a remote compute host and/or containers. It requires the path to the rpc inventory file, usually located at /etc/rpc_deploy/rpc_inventory.json. 
This options also requires the script be ran from the environments deployment host.

###Usage
```bash
./manageNeutron.py --source_file \<path\> debug -i \<path_to_inventory_file\> --restart_services
```
