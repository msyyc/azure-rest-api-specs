# Shared Swagger lint baseline

Use `current.json` for discovery. Resolve this branch once, record its exact
metadata commit, and read both descriptors at that commit. Keep the selected
baseline immutable throughout a migration.

The metadata commit is not the tested specs commit. The tested source is the
descriptor's `source.commit`, retained separately at
`evidence/long-running-operations-options-validator-20261022-source`.
Prepare a separate writable specs runtime at that source commit for each
parallel native candidate. Do not inject candidate packages into shared data.

The initial baseline contains 487 successful ARM projects, 649 Swagger files,
and 222905 observations. Its index lists 121 rules with findings, not every
enabled rule. Check production registration, audience, and activation before
interpreting an absent shard as zero. Data-plane and RPaaS coverage are not
established by this ARM run. `rule-registration.json` preserves the installed
ruleset declarations; declarations alone do not prove selector activation.

Download the checksummed release asset through the verified consumer in
[Azure/typespec-azure#5809](https://github.com/Azure/typespec-azure/pull/5809).
Follow its `analyze-native-lint-coverage/shared-baseline.md` instructions.
The consumer verifies compressed bytes, safe extraction, the full file
inventory, source identity, project completion, and observation counts.
Large datasets are release assets, not Git payloads.

`summary.json`, `validator-results.json`, and `rule-registration.json` are
compact saved evidence. The archive contains the complete dataset and a
Swagger-only sealed manifest. Machine-specific path prefixes are replaced in a
copy, with source/published hashes retained in the sanitization receipt.
The original dataset is unchanged. No native completion or semantic equivalence
is claimed by this publication.

Normal migrations reuse the selected Swagger observations and run native
analysis afresh. Keep compiler/emitter/library compatibility checks, semantic
controls, gap investigation, and both review checkpoints. Incompatible or missing
data must block; do not silently regenerate Swagger.

A separately requested refresh resolves current source and toolchain refs,
validates the complete population, and publishes a new immutable version and
asset. Verify a downloaded copy before advancing `current.json`. Never replace
an older version or refresh a selected baseline during a migration.
