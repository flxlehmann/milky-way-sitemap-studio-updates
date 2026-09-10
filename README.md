# Milky Way update manifests

Public version announcements for Sitemap Studio and Milky Way Sitemap Viewer.
The applications have independent release versions:

| Application | Manifest | Download destination |
| --- | --- | --- |
| Sitemap Studio | [update.json](update.json) | Studio ZIP in its GitHub release |
| Milky Way Sitemap Viewer | [viewer.json](viewer.json) | [Confluence download page](https://collaboration.msi.audi.com/confluence/x/jhrLg) |

The existing Studio filename remains unchanged for compatibility. Each manifest
contains only `version`, `releaseUrl` and `downloadUrl`. Source code, project data
and release files are not stored in this public repository.

Applications check their manifest at startup, every five minutes and when the
user chooses to check for updates. A newer version produces a notification;
its download action opens the corresponding destination. In the Viewer,
checking for updates itself does not navigate to Confluence.

After publishing a GitHub release with its ZIP and SHA-256 checksum, run
`pnpm publish:update-manifest` from the corresponding application repository.
The command verifies the release and updates only that application's manifest.
It needs GitHub access to both repositories; the default Actions token cannot
write across repositories. GitHub caching can briefly delay a new announcement.

The Viewer ZIP must also be uploaded to Confluence manually. Updating this
manifest does not upload or replace that file.
