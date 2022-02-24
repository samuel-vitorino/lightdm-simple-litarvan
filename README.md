# Simple Litarvan's LightDM WebKit2 theme

A simpler version of Litarvan's LightDM WebKit2 theme without Setup, Desktop Environment selection and with a smaller and centered login form.

## [Live testing](https://samuel-vitorino.github.io/lightdm-simple-litarvan/)

# Installation

## Arch Linux (3.0.0)

* If not already done, edit `/etc/lightdm/lightdm.conf` and set `greeter-session=lightdm-webkit2-greeter` .
* Build and extract `lightdm-webkit-theme-simple-litarvan-3.2.0.tar.gz` to `/usr/share/lightdm-webkit/themes/simple-litarvan/` .
* Then edit `/etc/lightdm/lightdm-webkit2-greeter.conf` and set `theme` or `webkit-theme` to `simple-litarvan` .

# Building (3.2.0)

```
$ ./build.sh
```

Will generate a lightdm-webkit-theme-simple-litarvan-3.2.0.tar.gz in the current folder.

# Screenshots

![Splash screenshot](https://samuel-vitorino.github.io/lightdm-simple-litarvan/splash_view.png)

![Login screnshot](https://samuel-vitorino.github.io/lightdm-simple-litarvan/login_view.png)
