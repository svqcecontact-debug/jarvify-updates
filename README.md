# Jarvify updates

This repository exists so the Jarvify app can check for a new version.
It holds one manifest and the installers. There is no code here.

Jarvify fetches `latest.json` on launch, compares the version, and
verifies the sha256 of anything it downloads before running it.

Current version: **1.7.0**
