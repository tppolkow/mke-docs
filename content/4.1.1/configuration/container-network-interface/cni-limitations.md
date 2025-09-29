---
aliases:
  - /latest/configuration/container-network-interface/cni-limitations/
  - /docs/configuration/container-network-interface/cni-limitations/
title: Limitations
weight: 3
---

It is important to be familiar with the MKE 4k limitations related to Calico OSS CNI:

- IPVS not supported
- Only clusters that use the default Kubernetes proxier `iptables` can be
  upgraded from MKE 3 to MKE 4k.
- Only KDD-backed MKE 3 clusters can be upgraded to MKE 4k. Refer to [Upgrade
  from MKE 3.7 or 3.8](../../../upgrade-from-mke-3x) for more information.
