# Home Assistant Community Add-on: Tautulli

Tautulli monitors your Plex Media Server and turns its activity into detailed
watch history, user and library statistics, graphs, and notifications. It can
show who is streaming, what they are watching, where they are watching from,
and how each stream is being played.

## Getting started

After starting the add-on, select **Open Web UI** to launch Tautulli inside Home
Assistant. Home Assistant authenticates users before opening the Ingress page.
On first use, Tautulli's setup wizard will guide you through connecting Tautulli
to your Plex Media Server.

Once setup is complete, you can use Tautulli to:

- Monitor current Plex streams and playback details.
- Search and filter watch history.
- Compare statistics across users and libraries.
- Explore activity trends using configurable graphs.
- Create notifications for playback events and newly added media.

To keep Tautulli readily available, enable **Show in sidebar** on the add-on's
**Info** tab.

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Home Assistant add-on.

1. Click the Home Assistant My button below to open the add-on on your Home
   Assistant instance.

   [![Open this add-on in your Home Assistant instance.][addon-badge]][addon]

1. Click the "Install" button to install the add-on.
1. Start the "Tautulli" add-on.
1. Check the logs of the "Tautulli" add-on to see if everything went well.
1. Click "OPEN WEB UI" to open Tautulli and follow the setup wizard.

**NOTE**: Starting the add-on might take a couple of minutes (especially the
first time starting the add-on).

## Configuration

### Option: `api_access`

This option is enabled by default. It allows Home Assistant Core to reach only
Tautulli's `/api/v2` endpoint over Home Assistant's internal app network.
Tautulli validates those requests using the API key from **Settings** >
**Web interface**. Direct access to the web interface remains blocked when
`disable_authentication` is enabled.

#### Connect the Home Assistant Tautulli integration

1. In Tautulli, open **Settings** > **Web interface** and copy the API key.
1. In Home Assistant, open **Settings** > **Devices & services**.
1. Select **Add integration**, then select **Tautulli**.
1. Enter the following details for an installation from the official Home
   Assistant Community Add-ons repository:

```text
URL: http://a0d7b954-tautulli:8181
API key: <the API key shown in Tautulli>
Verify SSL certificate: off
```

For a copy installed in the local add-ons directory, use this URL instead:

```text
http://local-tautulli:8181
```

These are real DNS names on Home Assistant's private app network. Supervisor
builds an app identifier from its repository identifier and slug, such as
`local_tautulli`, then replaces underscores with hyphens to form the hostname
`local-tautulli`. The official repository identifier produces
`a0d7b954-tautulli`. These names normally resolve only from Home Assistant Core
and other apps, not from computers on the local network.

The internal hostname always uses container port `8181`. Changing the host port
shown on the add-on's **Network** tab does not change this internal URL. The
connection uses plain HTTP, but its traffic remains on Home Assistant's private
app network.

An installation from another add-on repository has a different generated
repository identifier. If its internal hostname is unknown, use
`http://<home-assistant-ip>:<mapped-port>` as a fallback, where `mapped-port` is
the host port assigned to `8181/tcp` on the **Network** tab. Do not use HTTPS
unless a separate TLS reverse proxy has explicitly been configured.

Set `api_access` to `false` and restart the add-on to block API access from Home
Assistant Core.

### Option: `disable_authentication`

This option is enabled by default. It skips Tautulli's redundant username and
password step during first-run setup and relies on Home Assistant to authenticate
users through Ingress.

Direct access on port `8181` is disabled while this option is enabled, because
Tautulli does not have its own authentication protecting that endpoint.

Set the option to `false`, provide `authentication_username` and
`authentication_password`, and restart the add-on to enable authentication and
direct access. NGINX enforces these credentials before forwarding direct
requests to Tautulli. Tautulli's own authentication remains disabled to avoid a
second login prompt. Changing authentication settings inside Tautulli therefore
cannot expose the direct port without a password.

### Option: `authentication_username`

The username NGINX requires for direct access when `disable_authentication` is
`false`.

### Option: `authentication_password`

The password NGINX requires for direct access when `disable_authentication` is
`false`. The password is masked in the Home Assistant configuration UI. Change
direct-access credentials in the add-on options rather than in Tautulli.

If either credential is missing, the add-on starts in its safe ingress-only mode
and keeps direct access blocked.

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```yaml
disable_authentication: true
api_access: true
log_level: info
```

### Option: `log_level`

The `log_level` option controls the level of log output by the addon and can
be changed to be more or less verbose, which might be useful when you are
dealing with an unknown issue. Possible values are:

- `trace`: Show every detail, like all called internal functions.
- `debug`: Shows detailed debug information.
- `info`: Normal (usually) interesting events.
- `warning`: Exceptional occurrences that are not errors.
- `error`: Runtime errors that do not require immediate action.
- `fatal`: Something went terribly wrong. Add-on becomes unusable.

Please note that each level automatically includes log messages from a
more severe level, e.g., `debug` also shows `info` messages. By default,
the `log_level` is set to `info`, which is the recommended setting unless
you are troubleshooting.

## Access

The recommended way to use Tautulli is through **Open Web UI** or the Home
Assistant sidebar. Both use Home Assistant Ingress and do not require Tautulli
to be exposed outside your Home Assistant instance.

## Embedding into Home Assistant

Tautulli supports Home Assistant Ingress and can be opened directly inside the
Home Assistant frontend. On the add-on's **Info** tab, enable
**Show in sidebar**. No `panel_iframe` configuration or externally exposed port
is required.

The add-on configures Tautulli's HTTP root automatically. If you previously set
an HTTP root in Tautulli, restart the add-on so it can restore the correct
Ingress path.

## Changelog & Releases

This repository keeps a change log using [GitHub's releases][releases]
functionality.

Releases are based on [Semantic Versioning][semver], and use the format
of `MAJOR.MINOR.PATCH`. In a nutshell, the version will be incremented
based on the following:

- `MAJOR`: Incompatible or major changes.
- `MINOR`: Backwards-compatible new features and enhancements.
- `PATCH`: Backwards-compatible bugfixes and package updates.

## Support

Got questions?

You have several options to get them answered:

- The [Home Assistant Community Add-ons Discord chat server][discord] for
  installation, add-on, and Home Assistant integration questions.
- The [Home Assistant Discord chat server][discord-ha] for general Home
  Assistant discussions and questions.
- The Home Assistant [Community Forum][forum].
- Join the [Reddit subreddit][reddit] in [/r/homeassistant][reddit]

For problems with this add-on, you can also [open an issue here][issue]. Include
the add-on logs and remove any tokens or other private information before
posting them.

For questions about Tautulli features or its Plex integration, use the upstream
[Tautulli Wiki][tautulli-wiki], [FAQ][tautulli-faq], or
[Discord community][tautulli-discord].

## Authors & contributors

The original setup of this repository is by [Joakim Sørensen][ludeeus].

For a full list of all authors and contributors,
check [the contributor's page][contributors].

## License

MIT License

- Copyright (c) 2018-2019 Joakim Sørensen
- Copyright (c) 2019-2025 Franck Nijhof

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[addon-badge]: https://my.home-assistant.io/badges/supervisor_addon.svg
[addon]: https://my.home-assistant.io/redirect/supervisor_addon/?addon=a0d7b954_tautulli&repository_url=https%3A%2F%2Fgithub.com%2Fhassio-addons%2Frepository
[contributors]: https://github.com/hassio-addons/addon-tautulli/graphs/contributors
[discord-ha]: https://discord.gg/c5DvZ4e
[discord]: https://discord.me/hassioaddons
[forum]: https://community.home-assistant.io/t/home-assistant-community-add-on-tautulli/68745
[issue]: https://github.com/hassio-addons/addon-tautulli/issues
[ludeeus]: https://github.com/ludeeus
[reddit]: https://reddit.com/r/homeassistant
[releases]: https://github.com/hassio-addons/addon-tautulli/releases
[semver]: https://semver.org/spec/v2.0.0.html
[tautulli-discord]: https://tautulli.com/discord
[tautulli-faq]: https://github.com/Tautulli/Tautulli/wiki/Frequently-Asked-Questions
[tautulli-wiki]: https://github.com/Tautulli/Tautulli/wiki
