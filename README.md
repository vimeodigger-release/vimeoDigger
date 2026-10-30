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

## External tools maintenance (2026-10-30)

The signed `VimeoDigger.exe` update replaces the application only. It does **not** install or update yt-dlp, FFmpeg or ffprobe. The application launches these from the `tools` directory beside its EXE, not from the system PATH. Keep the application at its existing path to preserve connection identity.

Verified stable versions for application 0.2.171:

- yt-dlp **2026.10.26**, upstream Windows x64 standalone: https://github.com/yt-dlp/yt-dlp/releases/tag/2026.10.26
- FFmpeg and ffprobe **9.0.2**, Gyan full shared Windows x64 release: https://www.gyan.dev/ffmpeg/builds/ (Windows provider linked by https://ffmpeg.org/download.html).

Verified SHA-256:

| Download | SHA-256 |
|---|---|
| `yt-dlp.exe` (2026.10.26) | `f5389d3698ecde4ef06f4e6b1ce0294fe9ac1396228c8990b8d3416d6d177a7d` |
| `ffmpeg-release-full-shared.7z` (9.0.2) | `4d2060a8b34a940aa47d785142055bb92a63053781e55f2ace4546edd519a8f5` |

Check yt-dlp against the release's `SHA2-256SUMS` and FFmpeg against the provider's `.sha256` file. The FFmpeg `release` URL is mutable: if its version or hash changes, do not treat it as this verified build or bypass a mismatch.

### Update an existing installation

1. Finish active downloads/conversions and close Vimeo Digger. Back up the entire existing `tools` directory outside the new `tools` directory. Do not move the application or change settings, data, pairing keys or the system PATH.
2. Prepare a new `tools` directory containing the verified `yt-dlp.exe`, and `ffmpeg.exe`, `ffprobe.exe` plus **all DLLs from the same FFmpeg archive's `bin` directory**. Do not mix old and new FFmpeg DLL families. `ffplay.exe` is not required.
3. Keep upstream licenses/notices: yt-dlp `LICENSE` and `THIRD_PARTY_LICENSES.txt` from the matching release, and FFmpeg archive `LICENSE` and `README.txt`. The FFmpeg README identifies its exact source revision and build configuration.
4. Replace only the application's `tools` directory with that prepared directory. Keep the old directory for rollback. Reopen the same application EXE.
5. Confirm `tools/yt-dlp.exe --version`, `tools/ffmpeg.exe -version` and `tools/ffprobe.exe -version`. Use only owned or authorized media for a download/preview test.

The verified local test used an owned synthetic HLS fixture, the application's real `Media.Prepare` implementation, yt-dlp acquisition, FFmpeg scene selection/transcoding/thumbnail generation and ffprobe validation: four-second silent H.264 preview, 96 frames. This does not claim a Vimeo account/cookie or live Vimeo extractor test.

### Historical downloads

Older Dropbox ZIP, source ZIP, PDF and Notion instructions have not been republished by this maintenance. In particular, an old full ZIP does not become current when the EXE auto-updates. Use the current signed GitHub release for the application and the separate verified upstream tool procedure above. Do not describe historical downloads as the current security-maintained package.

### 日本語

アプリの署名付き自動更新はEXEだけを更新し、外部ツールは更新しません。取得・変換の終了後にアプリを閉じ、既存の `tools` を別の場所へ退避し、検証済みyt-dlpとFFmpeg/ffprobeおよび同じ配布アーカイブのDLL一式・ライセンスを新しい `tools` に配置してください。旧DLLとの混在は禁止です。EXEの場所、設定、DB、ペアリング鍵、システムPATHは変更しません。上記ハッシュとバージョンを確認して同じEXEを再起動してください。旧Dropbox ZIP/PDF/Notionは今回更新しておらず、最新版一式として扱わないでください。
