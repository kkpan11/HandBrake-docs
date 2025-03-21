---
Type:            article
Title:           Where to get HandBrake
Project:         HandBrake
Project_URL:     https://handbrake.fr/
Project_Version: 1.9.0
Language:        English
Language_Code:   en
Authors:         [ Bradley Sepos <bradley@bradleysepos.com> (BradleyS) ]
Copyright:       2024 HandBrake Team
License:         Creative Commons Attribution-ShareAlike 4.0 International
License_Abbr:    CC BY-SA 4.0
License_URL:     https://handbrake.fr/docs/license.html
---

Where to get HandBrake
======================

## HandBrake releases and nightly builds

Official [HandBrake releases](https://handbrake.fr/downloads.php) and [nightly builds](https://github.com/HandBrake/HandBrake-snapshots) are available for Linux, Mac, and Windows.

HandBrake is open-source software licensed under the GNU General Public License Version 2 (GPLv2)[^license]. Anyone can download and use HandBrake *for free*.

<!-- .system-linux -->

For linux users, we provide FlatPak bundles which are available for download on our site, or via <a href="https://flathub.org/apps/details/fr.handbrake.ghb">flathub.org</a>

Users of other BSD- and *nix-like distributions may compile from source.

<!-- /.system-linux -->

HandBrake source code is available at the official [HandBrake repository on GitHub](https://github.com/HandBrake/HandBrake).

Other versions obtained via third parties are not supported.

## Warning about scams and fakes

HandBrake is available for *free* at the [HandBrake website](https://handbrake.fr/).[^checksums] This is the *only* official download source for HandBrake.

Beware of third-party websites and peer-to-peer downloads of HandBrake. They may include unwanted extras such as additional applications, [ransomware](https://en.wikipedia.org/wiki/Ransomware), or other forms of [malware](https://en.wikipedia.org/wiki/Malware). The HandBrake Team has no control over these external services. Avoid!

Beware of online marketplaces and auction sites. HandBrake is *free software*.

<!-- .system-linux -->

## Warning about broken third-party builds

Certain BSD/Linux distributions and package repositories create their own versions of HandBrake. These modified versions are often crippled (features removed for political reasons) and broken (bugs due to modifications), and should be avoided.

Broken third-party packages/builds include but are not limited to:

- Debian Multimedia: `handbrake`, `handbrake-cli`, `handbrake-gtk`
- FreeBSD: `handbrake`
- Gentoo: `handbrake`
- NixOS: `handbrake`
- openSUSE Packman: `handbrake`, `handbrake-cli`, `handbrake-gtk`
- RPM Fusion: `handbrake`, `handbrake-cli`
- Ubuntu Universe: `handbrake`, `handbrake-cli`, `handbrake-dbg`
- Void: `handbrake`, `handbrake-cli`, `handbrake-cli-dbg`, `handbrake-dbg`

Please **do not** request support for these or any other unofficial versions. The HandBrake Team has zero control over them and therefore cannot provide meaningful support.

<!-- /.system-linux -->

<!-- .continue -->

## Next steps

<!-- .success -->

Continue to [Downloading and installing HandBrake](download-and-install.html).

<!-- /.success -->

<!-- /.continue -->

[^license]: For more information about the license, see the [LICENSE](https://github.com/HandBrake/HandBrake/blob/master/LICENSE) file and a [summary of GPLv2 on TLDRLegal](https://tldrlegal.com/license/gnu-general-public-license-v2).

[^checksums]: Downloaded files should match the [official release checksums](https://handbrake.fr/checksums.php) as published on the official HandBrake website. Downloaded files with unlisted checksums may be tampered with.
