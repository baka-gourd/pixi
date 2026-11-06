# Standalone distribution metadata

This directory vendors the crates.io `uv-client` 0.0.98 release from
https://github.com/astral-sh/uv (MIT OR Apache-2.0).

The local patch adds `RegistryClientBuilder::use_dist_info_metadata`, enabled by
default. When disabled, registry wheels use the existing HTTP range / streaming
metadata reader even if the index advertises PEP 658/714 metadata. Existing
parsed metadata caches remain reusable; index responses need no rewriting.

Pixi passes `pypi-config.use-dist-info-metadata` through every registry client
construction path. Remove this patch once the upstream crate exposes equivalent
configuration. Keep unrelated upstream source unchanged when updating it.
