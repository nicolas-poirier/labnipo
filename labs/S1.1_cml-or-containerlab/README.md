# S1.1 — CML or Containerlab on Proxmox

Lab used in the article *CML or Containerlab on Proxmox?*

## Topology

Headquarters and one branch office run on Cisco Modeling Labs; the provider network
runs on Containerlab with Nokia SR Linux. The boundary between both platforms is the
customer / provider demarcation.

| Device | Platform | Image | OOB address |
|---|---|---|---|
| `hq-rtr-01` | CML | IOL XE 17.18.02 | 10.255.0.31 |
| `hq-dst-01` | CML | IOL-L2 XE 17.18.02 | 10.255.0.11 |
| `br1-rtr-01` | CML | IOL XE 17.18.02 | 10.255.0.41 |
| `br1-sw-01` | CML | IOL-L2 XE 17.18.02 | 10.255.0.21 |
| `isp-pe-01` | Containerlab | SR Linux 26.7.2 | 10.255.0.151 |
| `isp-pe-02` | Containerlab | SR Linux 26.7.2 | 10.255.0.152 |

## Tested versions

Proxmox VE 9.2.20 · CML 2.10.0+build.13 · Containerlab 0.81.1 ·
SR Linux 26.7.2 · IOL XE 17.18.02

## Deploying the provider network

```bash
docker pull ghcr.io/nokia/srlinux:26.7.2
sudo containerlab deploy -t clab/labnipo-wan.clab.yml
```

The topology expects two Linux bridges on the host, `br-interco-hq` and
`br-interco-br1`, carrying the VLANs that reach the CML side. Adjust or remove those
bridge nodes if you run the whole lab on a single machine.

## Deploying the campus

Import `cml/labnipo-campus.yaml` into CML, then paste the matching file from
`configs/` into each node before first boot. Cisco images are required and are not
provided here.
