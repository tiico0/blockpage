# PiPass
<a href="https://codeclimate.com/github/roenw/PiPass/issues">![Maintainability](https://api.codeclimate.com/v1/badges/9d4a537646feea510ddf/maintainability)</a>
![version](https://img.shields.io/github/release/pipass/blockpage.svg?label=release)
![GitHub issues](https://img.shields.io/github/issues-raw/pipass/blockpage.svg?color=blue)
![GitHub pull-requests](https://img.shields.io/github/issues-pr-raw/pipass/blockpage.svg?color=green)

PiPass is an extention to the Pi-Hole project which adds easy temporary unblocking functionality and a visually appealing blockpage. The whole project currently is written in PHP, so it will integrate very easily with your existing Pi-Hole system. The blockpage is very easy to use, presenting three distinct options, an automated, temporary unblock button among them.

<p align="center">
  <a href="https://apps.roen.us/pipass/blockpage.png"><img src="https://apps.roen.us/pipass/blockpage.png" width="75%" height="75%"></a><br/>
  <strong>PiPass blockpage</strong><br />
</p>

Prerequisites
------
* Pi-Hole
* Root (sudo) access to system
* php-curl plugin, used to check for new versions of PiPass.
* Empty webroot - cannot contain index.html, index.php, etc.

Install
------
Installation on a vanilla Pi-Hole is completely automated. Execute ``bash <(wget -qO- https://sputnik.roen.us/pipass/scripts/install.sh)`` to install, and you should be done. Please make sure you have php-curl installed before running the install. Install it by executing ``sudo apt update && sudo apt install -y php-curl``.

If you have a more complex installation (e.g. using ``NGiNX`` as a webserver), follow these steps below.

1. Make your webserver redirect all 404 errors to the webroot. If you use ``lighttpd``, this function is automated.

For ``NGiNX``, this is

```
        location / {
                try_files $uri $uri/ =404;
                error_page 404 =200 http://$host;
        }
```

3. ``bash <(wget -qO- https://sputnik.roen.us/pipass/scripts/install.sh)`` - You may be prompted for elevated permissions using ``sudo``.
 (alternative https://raw.githubusercontent.com/PiPass/bin/master/install.sh)
4. Optional: fill out the ``config.php`` configuration file.

Contributing
------
PiPass is an open-source project and relies on community support to stay alive. You may find problems in the code, in which I would strongly encourage you to create an issue, or if you're willing to solve it yourself, fork the repository and create a pull request. If you want a feature added, feel free to [create an issue](https://github.com/roenw/PiPass/issues).


A list of known caveats is at the bottom of this document. If you'd like to contribute but don't know how, check there for some ideas.

Support
------
Having problems? [Let me know.](https://github.com/roenw/PiPass/issues)

**Do not ask questions in Pi-Hole communities as PiPass is a separate project.**

Pull requests are welcome!

Known Caveats
------
* Requires webroot index
* Will not work on websites supporting HSTS without a trusted self-signed certificate


Future Ideas
------
* Ability to trigger permanent whitelist after password entry
* Admin console for PiPass (currently being worked on)
* apt repository/package and Docker image
