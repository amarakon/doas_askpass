Doas AskPass
================

## Contents

-   [Usage](#usage)
-   [Dependencies](#dependencies)
-   [Installation](#installation)
    -   [Universal](#universal)
    -   [Gentoo](#gentoo)
-   [Uninstallation](#uninstallation)
    -   [Universal](#universal-1)
    -   [Gentoo](#gentoo-1)
-   [Configuration](#configuration)

Doas AskPass is a simple expect script that basically creates a
`sudo -A` equivalent for Doas. This allows you to graphically enter your
password.

## Usage

    `# user` doas-askpass <command>

## Dependencies

1.  Doas
2.  Expect

Dmenu is also recommended.

## Installation

### Universal

``` sh
`# user` git clone https://github.com/amarakon/doas_askpass
`# user` cd doas_askpass
`# root` make install
```

### Gentoo

``` sh
`# root` eselect repository add amarlay git https://github.com/amarakon/amarlay
`# root` emerge --sync amarlay
`# root` emerge app-admin/doas_askpass
```

## Uninstallation

### Universal

``` sh
`# user` cd doas_askpass
`# root` make uninstall
```

### Gentoo

``` sh
`# root` emerge -c app-admin/doas_askpass
# Remove my overlay (optional)
`# root` eselect-repository remove -f amarlay
`# root` emerge --sync
```

## Configuration

The graphical program that is expected by the script is set by the
`DOAS_ASKPASS` environment variable. Otherwise, the default is
`dmenu -P -p password`. You need the
[password](https://tools.suckless.org/dmenu/patches/password/) patch in
order for this to work. I recomment using my
[version](https://github.com/amarakon/dotfiles/blob/master/etc/portage/patches/x11-misc/dmenu/dmenu-password-5.0.diff)
which is more secure. You can set the environment variable in
`~/.bashrc` or anywhere else that your shell is going to source. The
following is an example.

``` sh
DOAS_ASKPASS="dmenu -P -p password:"
```
