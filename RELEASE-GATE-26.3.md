# ISARN SMP Minecraft 26.3 — Combined Resource Pack Release Gate

Gate decision: **PASS** (asset-only release; no plugin JAR or server-world changes).
Runtime owner: **DREW**; Drew reported on September 25, 2026 (America/Los_Angeles) that the server's automatic resource-pack download is fixed and all three merged resources are operational in Minecraft. This report records the owner's statement; ChatGPT did not independently control the Minecraft client.

## Exact production artifact
- Repo: `DeathWish2253/IsarnResourcePack`
- Filename: `ISARN-Server-ResourcePack.zip`
- Final resource-pack content commit prior to this documentation-only record: `4e8ab87afca4afcfd166226b9dba95c49ecafc0f`
- Git blob SHA-1: `664a4b30872ad0fb8f027f764fac37ebaed2bc76`
- Bytes: `112114`
- ZIP SHA-1 / `resource-pack-sha1`: `7a7132799eba9e761889bf7549033a56143aa9e5`
- ZIP SHA-256: `af09a04a606bc2c4c76a9e89807fa01b8732ee609a61182232d97b26c209a222`
- Direct URL: https://raw.githubusercontent.com/DeathWish2253/IsarnResourcePack/main/ISARN-Server-ResourcePack.zip
- Original V1.5.6 portal ZIP retained alongside current combined ZIP for rollback.

## Baselines and component identity
- Portal original: `ISARNPortals-V1.5.6-Resource-Pack.zip`, main baseline `2d8734f30b1bc54e2e0bd88fb49a7e98bf0073d4`.
- Skills original: `ISARN-Skills-V1.22.18-ResourcePack.zip`, Skills authoritative `main` implementation V1.22.21 SHA `a18e8d1836fb0cd5cf0554870b27d4276534125a`, whose resource pack remained unchanged from V1.22.18.
- Clock original: clock model extracted from `ISARN-ResourcePack-26.3-ClockWhitelist-CANDIDATE.zip` after Drew's isolated client runtime PASS; accepted cases: `minecraft:world`, `minecraft:overworld`, `minecraft:resource` use `daytime`, every other dimension uses `random`.
- Unified pack metadata: `min_format` and `max_format` `[97,1]`; Minecraft Java 26.3.
- Initial merged candidate immutable content commit: `2235db121f966f91a10066a38fa782e9763eae6c`.
- Candidate branch final audit index: https://github.com/DeathWish2253/IsarnResourcePack/blob/62cc40de94cb34ea175457908617461c39d7c133/MERGE-AUDIT-26.3.md

## Gate matrix
| Check | Result | Evidence |
|---|---|---|
| Authority/source baseline | PASS | Exact GitHub source versions and preserved older portal ZIP. |
| Complete static asset and packaging audit | PASS | 45 entries independently decompressed and CRC-verified, 23 JSON/mcmeta parse checks, 11 PNG signatures, required two Skills font PNG references, 26.3 pack metadata, no path collisions; recorded in immutable candidate audit. |
| Exact artifact equivalence | PASS | Production `main` ZIP Git blob `664a4b30872ad0fb8f027f764fac37ebaed2bc76` matches the independently audited merged candidate; unmodified ZIP bytes. |
| Combined three-component runtime | PASS (DREW) | Owner reported auto-download fixed and all three packs operational. |
| Artifact transport | PASS | Production file 112,114 bytes and available through the GitHub repository. |
| Repository preservation | PASS | Production copy in `main`, immutable candidate branch and audit, original portal resource pack retained. |
| Java 25/Paper API plugin build | N/A | No plugin source, Java source, or server plugin JAR modified. |
| Release approval | PASS | This independent ChatGPT static/evidence review plus Drew-owned runtime confirmation. |

Production operations: the pack is already live per Drew. Do not modify the production ZIP without starting a new resource-pack release iteration and repeating relevant audit/runtime gates. A documentation-only commit of this gate record does not change released ZIP bytes, SHA-1, or URL.
