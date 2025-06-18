# Nextcloud app store action

Download and/or get metadata of latest app version from Nextcloud app store.

## Inputs

### `appid`

**Required** Nextcloud app ID.

### `server_major`

**Optional** Nextcloud server major version number. (e.g. `31`)

### `download`

**Optional** Whether the app shall be downloaded. (default `false``)

### `apps_folder`

**Optional** Where to unpack the app. (default `apps`)

## Outputs

### `release`

Metadata of the latest app release compatible with specified Nextcloud version

### `version`

Version of the release

### `download`

Download URL of the release

## Usage

The action retrieves the metadata of the latest app version from the app store
ond optionally downloads and unpacks the release tarball.

It caches the app store `apps.json` file for a maximum of one hour to prevent
running into the appstore rate limits.

It's a wrapper around [nextcloud/appstore-action](https://github.com/nextcloud/appstore-action).

Here is an example that downloads the latest version of `collectives` that's
compatible with Nextcloud 30 and unpacks it to `apps-extra`:

```yaml
- name: Get collectives app from app store
  id: collectives_app
  uses: nextcloud/appstore-action@3df8d62ff6f2c264406409334f12c72756fcae39 # v1.0.0
  with:
    appid: collectives
    server_major: 31
    download: true
    apps_folder: apps_extra
```

## License

[MIT License](LICENSE)
