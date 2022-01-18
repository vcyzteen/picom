[**Click here for the official picom README**](https://github.com/yshui/picom)

## <p align="center">BEFORE</p>

<img src="https://i.postimg.cc/kD4KsWBG/2022-01-18-17-46-42-screenshot.png" />

## <p align="center">AFTER</p>

<img src="https://i.postimg.cc/DJYWHY8Z/2022-01-18-17-49-15-screenshot.png" />

## Why another picom fork?

**TL;DR:** rounded corners, upstream commit from yshui next base and dual_kawase blur on all backends.

### This fork contains:

- Dual kawase blur method from [tryone144](https://github.com/tryone144/compton) as well as his new [feature/dual_kawase branch](https://github.com/tryone144/compton/tree/feature/dual_kawase) which implements the dual kawase blur method on the experimental glx backend.

- Rounded corners code from [sdhand](https://github.com/sdhand/picom) which is also ported to the experimetnal XRender backend.

- New code for rounded corners (+borders) on the glx backend using GLSL fragment shader for both legacy and experimental backends

For more information read [ibhagwan reddit post](https://www.reddit.com/r/unixporn/comments/fs8trg/oc_comptonpicom_fork_with_both_tryone144s_dual/)

## How to install

Clone this repo and follow the [build instructions of the official picom README](https://github.com/yshui/picom/blob/next/README.md#build)


## 2021-02-05 Update

It's been a while since this fork had some work and the good people at [the main picom branch](https://github.com/yshui/picom) merged some of this code into the main branch.

However, not all code / features have been merged, ATM the status is as per the below:


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
