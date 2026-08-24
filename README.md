# Home Assistant Community Add-on: Tautulli

[![GitHub Release][releases-shield]][releases]
![Project Stage][project-stage-shield]
[![License][license-shield]](LICENSE.md)

![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]

[![Github Actions][github-actions-shield]][github-actions]
![Project Maintenance][maintenance-shield]
[![GitHub Activity][commits-shield]][commits]

[![Discord][discord-shield]][discord]
[![Community Forum][forum-shield]][forum]

Monitor, understand, and get notified about activity on your Plex Media Server.

![Screenshot][screenshot]

## About

Tautulli is a web application for monitoring, analytics, and notifications for
[Plex Media Server][plex]. This add-on packages Tautulli so it can run alongside
Home Assistant and open directly from the Home Assistant sidebar.

With Tautulli you can:

- Monitor current Plex streams, including users, devices, quality, and location.
- Explore watch history and detailed statistics for users and libraries.
- View configurable graphs, popular content, and server activity trends.
- Send customizable notifications for playback activity and newly added media.
- Use a responsive interface on desktop, tablet, and mobile browsers.

## Before you install

- A working Plex Media Server is required; this add-on does not include Plex.
- The first start can take a few minutes while Tautulli is initialized.
- Tautulli guides you through connecting to Plex when you first open the Web UI.
- Home Assistant Ingress is used by default. Direct access on port `8181` is
  enabled only when `disable_authentication` is `false` and both authentication
  credentials are configured. Otherwise, use Home Assistant Ingress. NGINX
  enforces direct credentials independently of Tautulli's settings.
- Home Assistant Core can access Tautulli's API over the private app network;
  the web interface remains protected by Home Assistant Ingress.

This add-on stores its Tautulli configuration and database in the add-on data
directory, where they are included in Home Assistant add-on backups.

[:books: Read the full add-on documentation][docs]

## Support

Got questions?

You have several options to get them answered:

- The [Home Assistant Community Add-ons Discord chat server][discord] for
  installation, add-on, and Home Assistant integration questions.
- The [Home Assistant Discord chat server][discord-ha] for general Home
  Assistant discussions and questions.
- The Home Assistant [Community Forum][forum].
- Join the [Reddit subreddit][reddit] in [/r/homeassistant][reddit]

For problems with this add-on, you can also [open an issue here][issue]. For
questions about Tautulli itself, see the upstream [Tautulli Wiki][tautulli-wiki],
[FAQ][tautulli-faq], or [Discord community][tautulli-discord].

## Contributing

This is an active open-source project. We are always open to people who want to
use the code or contribute to it.

We have set up a separate document containing our
[contribution guidelines](.github/CONTRIBUTING.md).

Thank you for being involved! :heart_eyes:

## Authors & contributors

The original setup of this repository is by [Joakim Sørensen][ludeeus].

For a full list of all authors and contributors,
check [the contributor's page][contributors].

## We have got some Home Assistant add-ons for you

Want some more functionality to your Home Assistant instance?

We have created multiple add-ons for Home Assistant. For a full list, check out
our [GitHub Repository][repository].

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

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[commits-shield]: https://img.shields.io/github/commit-activity/y/hassio-addons/addon-tautulli.svg
[commits]: https://github.com/hassio-addons/addon-tautulli/commits/main
[contributors]: https://github.com/hassio-addons/addon-tautulli/graphs/contributors
[discord-ha]: https://discord.gg/c5DvZ4e
[discord-shield]: https://img.shields.io/discord/478094546522079232.svg
[discord]: https://discord.me/hassioaddons
[docs]: https://github.com/hassio-addons/addon-tautulli/blob/main/tautulli/DOCS.md
[forum-shield]: https://img.shields.io/badge/community-forum-brightgreen.svg
[forum]: https://community.home-assistant.io/t/home-assistant-community-add-on-tautulli/68745
[github-actions-shield]: https://github.com/hassio-addons/addon-tautulli/workflows/CI/badge.svg
[github-actions]: https://github.com/hassio-addons/addon-tautulli/actions
[issue]: https://github.com/hassio-addons/addon-tautulli/issues
[license-shield]: https://img.shields.io/github/license/hassio-addons/addon-tautulli.svg
[ludeeus]: https://github.com/ludeeus
[maintenance-shield]: https://img.shields.io/maintenance/yes/2025.svg
[plex]: https://www.plex.tv/media-server-downloads/
[project-stage-shield]: https://img.shields.io/badge/project%20stage-experimental-yellow.svg
[reddit]: https://reddit.com/r/homeassistant
[releases-shield]: https://img.shields.io/github/release/hassio-addons/addon-tautulli.svg
[releases]: https://github.com/hassio-addons/addon-tautulli/releases
[repository]: https://github.com/hassio-addons/repository
[screenshot]: https://github.com/hassio-addons/addon-tautulli/raw/main/images/screenshot.png
[tautulli-discord]: https://tautulli.com/discord
[tautulli-faq]: https://github.com/Tautulli/Tautulli/wiki/Frequently-Asked-Questions
[tautulli-wiki]: https://github.com/Tautulli/Tautulli/wiki
