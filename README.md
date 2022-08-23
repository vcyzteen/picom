[**Click here for the official picom README**](https://github.com/yshui/picom)

## <p align="center">BEFORE</p>


<img src="https://i.postimg.cc/44vPJ5G6/2022-01-18-17-46-42-screenshot.png" />

## <p align="center">AFTER</p>


<img src="https://i.postimg.cc/6qBd7kKd/2022-01-18-17-49-15-screenshot.png" />

## Why another picom fork?

**TL;DR:** rounded corners, ,trasition, upstream commit from yshui next base and dual_kawase blur on all backends.

### This fork contains:

- Dual kawase blur method from [tryone144](https://github.com/tryone144/compton) as well as his new [feature/dual_kawase branch](https://github.com/tryone144/compton/tree/feature/dual_kawase) which implements the dual kawase blur method on the experimental glx backend.

- Rounded corners code from [sdhand](https://github.com/sdhand/picom) which is also ported to the experimetnal XRender backend.

- New code for rounded corners (+borders) on the glx backend using GLSL fragment shader for both legacy and experimental backends

- Trasition Windows Animated from [Arian8j2](https://github.com/Arian8j2)

### Dependencies

Assuming you already have all the usual building tools installed (e.g. gcc, python, meson, ninja, etc.), you still need:

* libx11
* libx11-xcb
* libXext
* xproto
* xcb
* xcb-damage
* xcb-xfixes
* xcb-shape
* xcb-renderutil
* xcb-render
* xcb-randr
* xcb-composite
* xcb-image
* xcb-present
* xcb-xinerama
* xcb-glx
* pixman
* libdbus (optional, disable with the `-Ddbus=false` meson configure flag)
* libconfig (optional, disable with the `-Dconfig_file=false` meson configure flag)
* libGL, libEGL (optional, disable with the `-Dopengl=false` meson configure flag)
* libpcre (optional, disable with the `-Dregex=false` meson configure flag)
* libev
* uthash

On Debian based distributions (e.g. Ubuntu), the needed packages are

```
libxext-dev libxcb1-dev libxcb-damage0-dev libxcb-xfixes0-dev libxcb-shape0-dev libxcb-render-util0-dev libxcb-render0-dev libxcb-randr0-dev libxcb-composite0-dev libxcb-image0-dev libxcb-present-dev libxcb-xinerama0-dev libxcb-glx0-dev libpixman-1-dev libdbus-1-dev libconfig-dev libgl-dev libegl-dev libpcre2-dev libpcre3-dev libevdev-dev uthash-dev libev-dev libx11-xcb-dev meson
```

On Fedora, the needed packages are

```
dbus-devel gcc git libconfig-devel libdrm-devel libev-devel libX11-devel libX11-xcb libXext-devel libxcb-devel libGL-devel libEGL-devel meson pcre-devel pixman-devel uthash-devel xcb-util-image-devel xcb-util-renderutil-devel xorg-x11-proto-devel
```

To build the documents, you need `asciidoc`

### To build

```bash
$ git clone --single-branch --branch next-yshui --depth=1 https://github.com/vcyzteen/picom.git
$ cd picom
$ git submodule update --init --recursive
$ meson --buildtype=release . build
$ ninja -C build
```

Built binary can be found in `build/src`

If you have libraries and/or headers installed at non-default location (e.g. under `/usr/local/`), you might need to tell meson about them, since meson doesn't look for dependencies there by default.

You can do that by setting the `CPPFLAGS` and `LDFLAGS` environment variables when running `meson`. Like this:

```bash
$ LDFLAGS="-L/path/to/libraries" CPPFLAGS="-I/path/to/headers" meson --buildtype=release . build

```

As an example, on FreeBSD, you might have to run meson with:
```bash
$ LDFLAGS="-L/usr/local/lib" CPPFLAGS="-I/usr/local/include" meson --buildtype=release . build
$ ninja -C build
```

### To install

``` bash
$ sudo ninja -C build install
```

Default install prefix is `/usr/local`, you can change it with `meson configure -Dprefix=<path> build`

### Included in main branch

- Rounded corners on legacy backends (both "glx" and "xrender")
- Dual-kawase blur on experimental "glx" backend only

### Not-included in main branch

- Rounded corners with "--experimental-backends"
- Rounded borders on the legacy "glx" backend
- Rounded border rules on the legacy "glx" backend
- Dual-kawase blur on the legacy "glx" backend

### Updated fork

Just fork from ibaghwan and upstream commit from yshui ( official picom ) and upstream commit from another pull request

```sh
❯ git clone --single-branch --branch next-yshui --depth=1 https://github.com/vcyzteen/picom.git
```
