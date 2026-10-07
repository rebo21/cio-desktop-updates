# CIO Desktop Updates

Public Windows release downloads for the CIO Service Request desktop application.

This repository contains release documentation. Installers and update metadata belong in GitHub Releases. Application source code, server configuration, credentials and signing private keys must remain outside this public repository.

## Downloads

Download published Windows installers from [Releases](https://github.com/rebo21/cio-desktop-updates/releases).

There is no desktop release published here yet. Creating this repository alone does not enable automatic updates in existing installations.

## Desktop updates

The planned Tauri updater endpoint is:

```text
https://github.com/rebo21/cio-desktop-updates/releases/latest/download/latest.json
```

This address becomes available after a published release includes a valid `latest.json` asset. The desktop application must first be configured with the updater and its verification public key, then built and distributed to users.

See [RELEASING.md](RELEASING.md) for the release process.

## Security

Update signatures verify the downloaded installer. Keep the signing private key and password secret and backed up; never attach them to a release or commit them here.

Release files are public downloads. Access to protected CIO records must continue to require authentication and server-side authorization.

A Tauri updater signature is separate from Windows code signing. It does not by itself remove Windows SmartScreen prompts.

## Domain changes

Keep this repository's owner and name stable. Its update endpoint is independent of the website domain. Before changing the website address, publish and test a desktop update that supports the new address, and keep the old website available during the transition.
