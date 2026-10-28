# Scoop bucket for Pergament

[![Tests](https://github.com/24mu13/scoop-pergament/actions/workflows/ci.yml/badge.svg)](https://github.com/24mu13/scoop-pergament/actions/workflows/ci.yml) [![Excavator](https://github.com/24mu13/scoop-pergament/actions/workflows/excavator.yml/badge.svg)](https://github.com/24mu13/scoop-pergament/actions/workflows/excavator.yml)

A [Scoop](https://scoop.sh) bucket for the portable Windows build of
[Pergament](https://github.com/v3rm1n0/pergament), an offline reader for JW
Library publications (`.jwpub`).

## Install

```pwsh
scoop bucket add pergament https://github.com/24mu13/scoop-pergament
scoop install pergament/pergament
```

This puts `pergament` (the command line tool) on the `PATH` and adds a
**Pergament** shortcut to the Start menu under Scoop Apps. The Microsoft Edge
WebView2 Runtime is required; it comes with Windows 10 and 11.

`scoop update pergament` installs new releases. The library is kept in
`%APPDATA%\pergament`, so it survives updates and uninstalling.

## Updates

The manifest has `checkver` and `autoupdate`, and the Excavator workflow checks
for new Pergament releases daily at 03:20 UTC and commits the updated manifest
(version, download URL, extraction directory, and SHA256 hash).

Push the workflow to the repository's default branch and ensure GitHub Actions
is enabled. The workflow already requests `contents: write` and uses the built-in
`GITHUB_TOKEN`; no personal access token or extra secret is needed. Branch
protection or repository policies must allow its commits.

You can run it immediately from **Actions > Excavator > Run workflow**.
GitHub may delay scheduled runs, and disables scheduled workflows in public
repositories after 60 days without repository activity; re-enable the workflow
if that happens.

To update by hand, with Scoop installed:

```pwsh
.\bin\checkver.ps1 -App pergament -Update
```

## Issues

Problems with the app itself belong in
[v3rm1n0/pergament](https://github.com/v3rm1n0/pergament/issues); problems with
installing it through Scoop belong here.
