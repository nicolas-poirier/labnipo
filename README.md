# Labnipo

Lab topologies and device configurations backing the network automation series on
[nicolas-poirier.fr](https://nicolas-poirier.fr).

Labnipo is a fictional company used as a common thread across the articles: a
headquarters, one branch office, and a WAN delivered by a service provider.

## Layout

| Path | Contents |
|---|---|
| `labs/<article>/` | everything needed to rebuild the lab of one article |
| `labs/<article>/clab/` | Containerlab topologies |
| `labs/<article>/cml/` | Cisco Modeling Labs topology exports |
| `labs/<article>/configs/` | day-0 device configurations |
| `shared/` | material reused across articles |

Each article folder is frozen when the article is published. A later article that
extends the network copies the previous folder rather than editing it, so every
published article stays reproducible. Tags mark the state of each publication.

## Reproducing a lab

Containerlab topologies use freely redistributable images and can be deployed by
anyone. Cisco Modeling Labs topologies require CML and the Cisco reference platform
images, which are **not** included here and are not redistributable.

Each lab folder has its own README with tested versions and commands.

## Conventions

- Device names follow `<site>-<role>-<nn>`; provider devices are prefixed `isp-`.
- Internal addressing uses RFC 1918, provider links use RFC 5737, ASNs come from
  RFC 5398.
- No secrets: configurations contain placeholders such as `<LAB_USER>`.

## License

MIT, see `LICENSE`.
