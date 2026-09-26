# ISARN resource-pack merge — Minecraft Java 26.3

Status: STATIC AUDIT PASS; COMBINED CLIENT RUNTIME = DREW / PENDING; PRODUCTION GATE = FAILED until required runtime passes.
Operation: ChatGPT direct asset-only merge; Codex N/A; no plugin source, world files, or server deployment changed.

## Authority
- Resource-pack repository: `DeathWish2253/IsarnResourcePack`, unchanged authoritative `main` baseline `2d8734f30b1bc54e2e0bd88fb49a7e98bf0073d4`.
- Current server pack: `ISARNPortals-V1.5.6-Resource-Pack.zip`, Git blob `7ab5bdb0680a89a35cf8456b3b17ff845365248c`, SHA-256 `cbd356a847c7f0ce044dd6d704856410497d307caf0fe89d47aefef6654877e5`, 36,541 bytes.
- Skills authoritative implementation: `ISARNProgressionAndSkills` main `a18e8d1836fb0cd5cf0554870b27d4276534125a`, V1.22.21 Release Gate PASS per Skills issue #26. Its last applicable released resource pack remains `ISARN-Skills-V1.22.18-ResourcePack.zip`, Git blob `3f95b9978fc989b6b64d2021a578865ad62e01c7`, SHA-256 `8244670cb323eb3486e0a6b7e94d49c278c03b2d7c6d74bb06fa5364c4e4f0dc`, 76,310 bytes. Skills V1.22.21 specifically retained those resource-pack assets unchanged.
- Clock: exact `assets/minecraft/items/clock.json` from Drew's runtime-PASS isolated merged candidate `ISARN-ResourcePack-26.3-ClockWhitelist-CANDIDATE.zip` (candidate SHA-256 `8609c03765de8015522567c726d7c7161df8d7a3de01f40992ad9f680d325163`). Clock JSON SHA-256 `7a97f425d00387ce707072c8c0353c95e61983ddeba92700bd179f00ed7e153b`, exact DEFLATE SHA-256 `5998a67b89e2d8f9d364f3f0d5a2f3ae8df28eeab244e2b369b2ffe32cd81aae`.
- Earlier versioned Skills working-folder `resource-pack-v1.22.15/assets/isarn/font/skills.json` differs from the released V1.22.18 ZIP's embedded font JSON. The released V1.22.18 ZIP, not the older working folder, is the input authority. Its bitmap glyphs, font mappings, and PNGs were preserved exactly.

## Merge
- Candidate branch: `candidate/clock-skills-26.3-merged` created from the unchanged resource-pack main baseline; no merge into main.
- First candidate commit: `2235db121f966f91a10066a38fa782e9763eae6c`.
- Artifact: `ISARN-Server-ResourcePack-26.3-Clock-Skills-CANDIDATE.zip`.
- Artifact size: 112,114 bytes, below GitHub transport limits.
- Git blob: `664a4b30872ad0fb8f027f764fac37ebaed2bc76`.
- ZIP SHA-1 (use only after runtime PASS for server resource-pack-sha1): `7a7132799eba9e761889bf7549033a56143aa9e5`.
- ZIP SHA-256: `af09a04a606bc2c4c76a9e89807fa01b8732ee609a61182232d97b26c209a222`.
- 39 non-metadata portal ZIP entries preserved byte-for-byte by copying the exact original compressed payloads; four non-metadata Skills ZIP entries likewise preserved (Skills README, two shell PNGs, font JSON).
- Exact passed clock JSON copied via its verified raw compressed payload.
- One unified root `pack.mcmeta` specifies `min_format: [97,1]`, `max_format: [97,1]` for Minecraft Java 26.3. The old portal metadata version 88.0 is intentionally superseded. No other gameplay/plugin/world input altered.
- Total ZIP entries: 45; no duplicate asset paths or nested pack root.

## Independent final static verification
- Remote candidate ZIP fetched again from immutable first commit; Git blob identity reverified.
- SHA-1 and SHA-256 digests independently calculated on the exact remote bytes; hash routines passed reference-vector checks.
- All 45 members independently DEFLATE-decoded and CRC-32 validated against central directory; **PASS**.
- Root/local/central-directory integrity and safe unique paths: **PASS**.
- All 23 JSON/mcmeta resources parse: **PASS**.
- All 11 PNG signatures: **PASS**. Skills shell PNG dimensions 176x168 and 176x222: **PASS**.
- Skills font JSON glyphs and references to both packaged shell PNGs: **PASS**.
- Portal/Skills compressed member content matched the original source ZIPs: **PASS**.
- Clock matches accepted runtime candidate compressed bytes and verifies main `minecraft:world`, private `minecraft:overworld`, resource `minecraft:resource` daytime cases; every other dimension uses `random`: **PASS**.
- Minecraft 26.3 pack format verified against official Mojang release documentation: 97.1.
- Java 25/Paper API compilation or server plugin JAR: N/A (resource-pack-only change). Server currently uses Paper 26.3 build 41 according to Drew; no build/API dependency changed.
- Production deployment: N/A / not authorized by the request.

## Runtime / Git / release gate
- Prior standalone/isolated clock candidate client runtime: DREW PASS (main-world clock corrected; Nether spinning restored after isolated test).
- This **combined** candidate has not yet received runtime verification with all three subsystems together. Runtime owner: DREW. Required checks: portal visual models/textures, Skills UI font/shell/advancement interaction, daytime clock in each three Overworlds, random spinning in custom Nether and End worlds, clean client reload/reconnect and no pack/model errors.
- Gate categories: baselines PASS; static asset preflight PASS; packaging/full asset audit PASS; exact remote ZIP/hashes PASS; Git preservation candidate branch PASS; combined runtime BLOCKED; release approval GATE FAILED until runtime.
- Do not deploy or replace the original main ZIP yet. After Drew passes runtime on this exact SHA-1 ZIP, ChatGPT must independently review results and explicitly grant or deny the resource-pack Release Gate. No automatic merge into main.
