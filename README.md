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

- CSP Lab, Victor doc
 - <https://docs.openshift.com/container-platform/4.2/installing/installing_vsphere/installing-vsphere.html>
- OCP Assest
 - OCP Client mirror: <https://mirror.openshift.com/pub/openshift-v4/clients/ocp/>
- CSP LAB Victor user guide
 - <https://github.com/ibm-cloud-architecture/refarch-privatecloud/blob/master/Install_OCP_4.x.md>

- More Reading
 - Bare-metal: A single-tenant physical server. Not a virtual server running in multiple on shared hardware. 
  - <https://en.wikipedia.org/wiki/Bare-metal_server>
 - Hypervisor, Host and Guest machine
 - https://en.wikipedia.org/wiki/Hypervisor
- DHCP server.
 - https://www.youtube.com/watch?v=e6-TaH5bkjo

## CP4 App on OCP 4.2 on vSphere

## Cluster Sizing

**Node**|**#**|**CPU**|**RAM**|**DISK1**|**DISK2**|**DISK3**
:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:
Installer|1|4|16|120||
Bootstrap|1|4|16|200||
LB|1|4|16|120||
Master|3|16|32|300||
Worker|8|16|64|200||
Storage|3|4|16|200|500|
NFS|1|2|8|500||

## Cluster Creation

## Appendix
