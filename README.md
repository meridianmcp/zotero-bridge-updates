# zotero-bridge-updates

The update channel for the Meridian Zotero Bridge plugin (`meridian-zotero@usemeridian.us`).

- `update.json` is what Zotero reads. Each entry names a version, the release file, and its SHA-256.
- Each release holds one Mozilla-signed `.xpi`, built from a commit of
  [meridianmcp/Meridian](https://github.com/meridianmcp/Meridian) (`extensions/zotero-bridge`).

To publish a version, run **Actions > Release Zotero bridge > Run workflow** with the version (for
example `0.1.2`) and the Meridian commit that contains it. The workflow:

1. refuses the version if Mozilla or this repository already has it;
2. signs it with Mozilla's unlisted channel, using the repository secrets `WEB_EXT_API_KEY` and
   `WEB_EXT_API_SECRET`;
3. publishes the signed file as release `v<version>`;
4. adds the version to `update.json` and checks that both public URLs answer.

Nothing in this repository holds source code. The source is in Meridian.
