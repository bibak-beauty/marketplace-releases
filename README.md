# Toptalla Marketplace releases

Official Android APK distribution for Toptalla Marketplace (`com.toptalla.marketplace`).
This repository contains release instructions and public release assets. Application source code is maintained separately.

## Downloads

Download the latest published Android release using these stable links:

- Latest release (download the versioned APK under Assets): https://github.com/bibak-beauty/marketplace-releases/releases/latest
- Version metadata: https://github.com/bibak-beauty/marketplace-releases/releases/latest/download/latest.json
- Release history: https://github.com/bibak-beauty/marketplace-releases/releases

## Publishing an Android release

1. Prepare a signed release APK for `com.toptalla.marketplace`. Keep the signing identity compatible with existing installations and increase Android's `versionCode` for each update.
2. Name the APK with its version, for example `toptalla-1.0.0.apk` for tag `v1.0.0`. Use three numeric version components.
3. Create `latest.json` using the template below. Use the version name and version code from the actual APK, not the website package version. Point `apkUrl` to this specific release tag.
4. Open **Releases → Draft a new release**. Create a unique tag such as `v1.0.0` and add a title and release notes.
5. Upload **both** the versioned APK and `latest.json` as release assets. Wait for uploads to finish before publishing.
6. For a production release, leave **This is a pre-release** unchecked and select **Set as latest release**, then publish.
7. Verify the fixed download links above, the APK installation/update on an Android device, and download accessibility from the networks your customers use.

Create a new release for each update and retain the previous releases. Keep `latest.json` named consistently and name each APK `toptalla-VERSION.apk`. The marketplace download route resolves the latest release tag to its matching versioned APK, so future releases need no website redeployment.

### Version metadata template

Illustrative values only; replace them with values from the APK being published:

```json
{
  "versionName": "1.0.0",
  "versionCode": 1,
  "apkUrl": "https://github.com/bibak-beauty/marketplace-releases/releases/download/v1.0.0/toptalla-1.0.0.apk"
}
```

The version metadata is a proposed contract for the app's update check; publishing it alone does not implement an update prompt. The application must compare its installed Android version code with `versionCode` and offer Google Play or direct download when an update is available. A web-based check must account for GitHub's cross-origin response behavior, for example by reading the manifest through a same-origin server route.

The direct download installs through Android's normal package installer. Website-only changes do not require a new APK.

Only upload public distribution files and release notes here. Never upload signing keystores, credentials, or private application source code.
