# Vimeo Digger releases

Windows release binaries and signed update metadata for Vimeo Digger.

This distribution-only repository does not contain application source, user data, credentials or private signing keys.

## Release assets

- `VimeoDigger.exe`: Windows x64 application
- `update.json`: version, target, size and SHA-256 manifest
- `update.sig`: RSA-PSS/SHA-256 signature verified against the public key embedded in the application

The application checks for updates approximately once every 24 hours. Acquisition preserves the saved automatic-download preference. Applying an update never triggers an unapproved restart.

Author: shimodatami
