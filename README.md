# Vimeo Digger releases

Windows release binaries and signed update metadata for Vimeo Digger.

This distribution-only repository does not contain application source, user data, credentials or private signing keys.

## Release assets

- `VimeoDigger.exe`: Windows x64 application
- `update.json`: version, target, size and SHA-256 manifest
- `update.sig`: RSA-PSS/SHA-256 signature verified against the public key embedded in the application

The application checks for updates approximately once every 24 hours. Acquisition preserves the saved automatic-download preference. Applying an update never triggers an unapproved restart.

Author: shimodatami

## Security maintenance: 0.2.171

- Updated bundled .NET 8 runtime to 8.0.33.
- Microsoft.Data.Sqlite and ProtectedData 10.0.14; WebView2 1.0.4314.35; QRCoder 1.8.1.
- Includes the local interface and database-readiness fixes following 0.2.163.
- Existing settings, authentication, pairing and group protocols are preserved.
- Distribution remains limited to the signed application and its update manifest/signature.
