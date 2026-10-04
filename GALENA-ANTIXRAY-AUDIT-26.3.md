# ISARN SMP 26.3 Galena anti-Xray candidate — static packaging audit

Status: **STATIC / PACKAGING PASS; CLIENT RUNTIME = DREW / PENDING; RELEASE GATE = FAILED until runtime**.

## Baseline
- Repository: `DeathWish2253/IsarnResourcePack`
- Production main: `03054a07b6577c29506a5b5013ee9e86aba3df49`
- Production artifact: `ISARN-Server-ResourcePack.zip`
- Production Git blob: `664a4b30872ad0fb8f027f764fac37ebaed2bc76`
- Production bytes: `112114`
- Production ZIP SHA-1: `7a7132799eba9e761889bf7549033a56143aa9e5`
- Production ZIP SHA-256: `af09a04a606bc2c4c76a9e89807fa01b8732ee609a61182232d97b26c209a222`
- Prior production Release Gate/runtime: PASS.

## Anti-Xray selection
- Project: **Galena** by Luracasmus.
- Upstream commit: `3996ef4cc145c0f357aa4606068ffbbe75ff0c83` (`v1.0.1+42.88`).
- Upstream `pack.mcmeta` blob: `e46956c25ad1c459f00358983501836bfe773f54`.
- Upstream license blob: `0cbb5e5d04f219f5b1ca211629e5d7d8c425d986`.
- License: MIT.
- Integration method: Galena's three `filter.block` rules only; no textures/models/shaders imported.

## Candidate
- Branch: `candidate/galena-antixray-26.3`
- Filename: `ISARN-Server-ResourcePack-26.3-Galena-AntiXray-CANDIDATE.zip`
- Entries: **46**.
- Candidate bytes: **114071**.
- ZIP SHA-1 / prospective `resource-pack-sha1`: `b6bedf2426aa4021a3d5471986a2fe23c38afc66`
- ZIP SHA-256: `a86725612cbe6f9c116f468920c46a9ec6a0dfbb53d7d0cab8b217dc7b621fd8`
- Git blob: `504bd911ec5f62cfd0ccfc07c940b10f7b3c8359`

## Static audit
- Exact production input size/hash verification before transformation: PASS.
- Original central-directory parse: 45 unique entries: PASS.
- All **44 non-`pack.mcmeta` production local-file records copied byte-for-byte**, including existing compressed payloads/descriptors: PASS.
- Portals, Skills UI/font/shell, and clock asset bytes therefore unchanged: PASS.
- Root `pack.mcmeta` replaced with Minecraft Java 26.3 metadata `min_format: [97,1]`, `max_format: [97,1]`: PASS.
- Galena filter block contains exactly the three upstream rules: PASS.
- `THIRD_PARTY_LICENSES/Galena-MIT.txt` contains required copyright/permission notice and upstream provenance: PASS.
- No duplicate ZIP paths: PASS.
- Candidate central-directory/local-header structure: PASS.
- New manifest/license CRC-32 validation: PASS.
- No anti-Xray texture/model/shader payload added: PASS.
- Artifact transport: PASS (well below ordinary Git limits).

## Runtime
Runtime owner: **DREW**.

Required acceptance on the exact candidate SHA-1 above:
1. required server pack loads cleanly on Minecraft Java 26.3;
2. Portals visuals remain correct;
3. Skills UI/font/shell remains correct;
4. clocks retain the accepted daytime/random behavior;
5. verify a representative common X-ray resource pack is materially blocked by Galena;
6. confirm no visible model/texture regressions or meaningful FPS regression.

Do not promote/replace the production ZIP on `main` until Drew runtime PASS and independent ChatGPT final gate review.
