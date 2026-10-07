# Publishing a Windows desktop update

## Initial setup

1. Configure the desktop updater in the private application repository, using the public release endpoint documented in README.md.
2. Generate and securely back up the updater signing key pair. Include only the verification public key in the desktop application.
3. Enable updater artifacts and implement the update prompt.
4. Build and test an initial updater-enabled Windows release. Existing installations without the updater need this release installed once before they can receive in-app updates.

Android releases are outside this repository's scope.

## Each release

1. Increase the desktop application's version and build the Windows updater artifacts with the same signing private key.
2. Test the installer and an upgrade from the previous updater-enabled version, including notification clicks and connection to the hosted application.
3. In this repository's Releases page, prepare a draft release with a matching version tag.
4. Attach the generated Windows installer and its signature file.
5. Attach a valid static Tauri update manifest named `latest.json`. Use the actual release version, the supported Windows target architecture, the exact HTTPS installer download URL and the generated signature contents. Follow the official schema; do not publish placeholder values.
6. Check all asset names and URLs, then publish the release as the latest stable release only when the complete asset set is ready.
7. Check the public endpoint and update an older installed desktop version to verify the download and installation.

The installer filename depends on the existing build configuration. Preserve its actual generated name rather than assuming a generic filename.

## Release safeguards

- Store build output as release assets rather than committing executables to Git history.
- Keep production credentials, private source, access tokens and signing private keys out of release files.
- Do not embed a GitHub access token in the desktop application; public downloads require no repository token.
- Restrict repository write access to trusted maintainers.
- Keep older release assets available. Do not replace an installer in an already published version with a different build.
- Use higher versions for fixes. If a release has a problem, pause distribution and publish a corrected version after testing.
- Automated publishing is not configured by this repository setup.

## Reference

[Tauri updater documentation](https://v2.tauri.app/plugin/updater/)
