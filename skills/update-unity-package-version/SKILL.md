---
name: update-unity-pkg-version
description: Update the installed version of a Unity package.
---

Update the installed version of the package indicated by the user.
Ask the user which package they want to update if not explicitly provided.
Edit the `Packages\manifest.json` and `Packages\packages-lock.json` files directly.
After editing them, use the Unity `refresh_asset_database` tool.

Workflow:

- When the package is installed via git, use `git ls-remote` to determine the latest commit, and update the pinned hash in `packages-lock.json`.
	- If the git package can't be updated this way, simply delete its entry from `packages-lock.json`. This will force Unity to download the latest package version.
- When the package is a Unity Engine package (`com.unity.X`), research which is the latest version of the package, and update the entry in `manifest.json`.
