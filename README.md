# CPAK on OCP Infra and Install<!-- omit in toc -->

## Table of Contents <!-- omit in toc -->
- [Objectives](#objective)
- [References](#references)
- [CP4 App on OCP 4.2 on vSphere](#icpa-ocp42-vsphere)
  - [Cluster Sizing](#icpa-cluser-sizing)
  - [Cluster Creation](#icpa-cluster-creation)
- [Appendix](#appendix)


## Objectives

This document objectives are:

## References
- This doc/template borrowed from: 
  - https://ibmcase.slack.com/archives/CRTL16GF7/p1581192646043300
- vCenter Server:
  - https://demo-vcenter.csplab.local/ui
- CSP LAB -  Victor install guide:
  - <https://github.com/ibm-cloud-architecture/refarch-privatecloud/blob/master/Install_OCP_4.x.md>
- RH OCP:
  - OCP Install: <https://docs.openshift.com/container-platform/4.2/installing/installing_vsphere/installing-vsphere.html>
  - OCP Client mirror: <https://mirror.openshift.com/pub/openshift-v4/clients/ocp/>
- GSE Asset - IBM Knowledege Center
  - OCP 3.11: http://cloudpak8s.io/
  - OCP 4.2:  http://ocp42.cloudpak8s.io/
  - OCPA Install Home: https://www.ibm.com/support/knowledgecenter/SSCSJL_3.x/install-icpa-cli.html

- More Reading
  - Bare-metal: A single-tenant physical server. Not a virtual server running in multiple on shared hardware. 
    - <https://en.wikipedia.org/wiki/Bare-metal_server>
  - Hypervisor, Host and Guest machines
    - <https://en.wikipedia.org/wiki/Hypervisor>
  - DHCP server.
    - <https://www.youtube.com/watch?v=e6-TaH5bkjo>
    
  - Utils:
    - VIDEO TO WATCH K8s Architecture: https://www.youtube.com/watch?v=_3NUI5vasPk
    - vi cheat sheet: <http://www.atmos.albany.edu/daes/atmclasses/atm350/vi_cheat_sheet.pdf>

## CP4 App on OCP 4.2 on vSphere

## Cluster Sizing

**Node**|**#**|**CPU**|**RAM**|**DISK1**|**DISK2**|**DISK3**
:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:
Installer|1|4|16|120||
Bootstrap|1|4|16|100||
LB|1|4|16|120||
Master(Control plane) |3|16|32|300||
Worker (Compute) |8|16|64|200||
Storage|3|4|16|200|500|
NFS|1|2|8|500||

## Cluster Creation
Web Server: http://172.18.3.227/res-cpsandbox/. TODO: UPDATE
Set up Installer: 
1. Create installer from installer template using OCP network.
2. Provide Alec with mac address to get IP address assigned.
3. Start installer VM and log in as sysadmin
4. Disable firewall. 
5. Make dir (mkdir /opt/sysadmin)
6. httpd server already installed in template. 
7. OC Client and installer binaries are available in template. 
8. Extract files into /opt
9. Copy kubectl and oc binaries into /usr/local/bin/
10. Generate SSH key
11. Add SSH key to ssh-agent
12. Backup install-config.yaml
13. Create manifests from install-config.yaml and ensure install-config.yaml is in the directory the openshift installer is referencing.
14. Set spec.mastersSchedulable to false in the manifests/cluster-scheduler-02-config.yml file
15. Create ignition files.
16. Create append-bootstrap.ign file. 
17. Base64 encode the ignition files for bootstrap, master and worker
18. Using RHCOS template, create bootstrap, master, worker nodes
19. Update VM with "disk.EnableUUID = TRUE", "Ignition config data encoding = base64" and "Ignition config data = Set to base64 encoding of ignition file"
20. Clone 3 master, 8 worker and 3 storage nodes 
21. Provision NFS server from NFS Server VM template.
22. Provide Alec with mac address to get IP address assigned for bootstrap, master, worker and storage nodes. 
23. Provision LB server from LB VM template.
24. Provide Alec with mac address to get IP address assigned for lb server. 
25. Start up lb server and edit haproxy.cfg.  Correct 3 typos and update file with master and compute IPs.
26. Create snapshot of bootstrap, master and compute VMs.
27. Start up boostramp, master and compute VM.
28. Run openshift-install command for boot-strap node or SSH to boostrap node to ensure etcd cluster comes up. 
29. Validate all nodes are coming up successfully. 
30. Set up Rook Ceph in cluster for image registry. 
31.

## Appendix
