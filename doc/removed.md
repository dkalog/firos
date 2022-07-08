# Removed Features

## REST-API `whitelist` on FIROS

FIROS had a REST-API, where someone could manipulate the whitelist of an FIROS-instance (see: [API](user/api.md)). We
removed this functionallity, because the `whitelist.json` is definitely known prior and is overwritten by the
configuration in `robots.json`.

Specifically, the following methods are no longer available:

-   `FIROS:/whitelist/write`
-   `FIROS:/whitelist/remove`
-   `FIROS:/whitelist/restore`
