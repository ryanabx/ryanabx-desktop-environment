# ryanabx desktop environment

## Why a new DE?

* I think it's fun to create new things
* Create a desktop environment that requires _less_ burden to maintain
  * Accomplish this by using components and apps that are already maintained in a group setting, thus improvements can be upstreamed very easily and everyone benefits.
    * "Stand on the shoulders of giants"
  * Treat a desktop environment as a software bundle that is known to work well together
* Use all rust stack for first-party components, and ideally all third-party components
  * Memory safety, etc
  * May not be able to accomplish this in the first iteration
    * Promote development of rust-based applications
* Use monolithic all-in-one shell
* Try to use layer-shell and other protocols as much as possible, so that hopefully any compositor will work with the shell, but it is not a goal to separate parts of the shell.

## What does a desktop environment need?

### Absolutely required (First party components):

#### Compositor

Use a smithay-based compositor

* Optional: Build a smithay-based compositor

Compositor and shell both work together to do things like workspace management, etc.

#### Shell Components

What's in the shell?

* Taskbar
* OSDs
* Launchers

#### Settings application

* Heavily related to the shell?
* Settings have to be paired with a daemon?
* Seems too custom to have a third-party solution

#### Settings daemon

* Will probably have to build a solution myself, afaik these don't follow any standards
* Integrate into the shell?

### Optional, but bundled with almost every installation

> **NOTE:** For this section, we want to choose the most self-contained options out there. We don't want for example a file manager that pulls in half of another desktop environment in order to have all its functionality. Rust-based solutions will hopefully excel in being self-contained.

#### Custom Portals implementation

* Probably can just reuse `xdg-desktop-portal-gtk`
* Investigate using custom portals implementation?

#### File Manager

* Options (Rust)
  * [cosmic-files](https://github.com/pop-os/cosmic-files)
* Options (Non-Rust)
  * [GNOME files](https://gitlab.gnome.org/GNOME/nautilus)
  * [Thunar](https://gitlab.xfce.org/xfce/thunar)

#### Terminal Emulator

* This has the most work done on it in rust
* Options (Rust)
  * [Alacritty](https://github.com/alacritty/alacritty)
  * [Wezterm](https://github.com/wez/wezterm)
  * [cosmic-term](https://github.com/pop-os/cosmic-term)
* Options (Non-Rust)
  * [Ptyxis](https://gitlab.gnome.org/chergert/ptyxis)

#### App Store

* Options (Rust)
  * [cosmic-store](https://github.com/pop-os/cosmic-store)
* Options (Non-Rust)
  * [GNOME Software](https://gitlab.gnome.org/GNOME/gnome-software)
  * [KDE Discover](https://invent.kde.org/plasma/discover)

## Additional goals

* Flatpak first
  * If there is a flatpak option for a component, go for it
  * Only shell/compositor/settings(could be flatpak?) should be installed normally
    * This minimizes the number of components to maintain in a distro
* Rust in all the first-party components
  * Provides additional safety