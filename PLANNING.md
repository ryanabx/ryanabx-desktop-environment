# ryanabx desktop environment

## Why a new DE?

* I think it's fun to create new things
* Create a desktop environment that requires _less_ burden to maintain
  * Accomplish this by using components that are already maintained in a group setting, thus improvements can be upstreamed very easily and everyone benefits.
  * Treat a desktop environment as a software bundle that is known to work well together
* Use all rust stack
  * Memory safety, etc
* Don't be modular
  * Modularity for third party components
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

#### Brightness / Volume management daemon

* Will probably have to build a solution myself, afaik these don't follow any standards
* Integrate into the shell?

#### Portals implementation

* Probably can just reuse `xdg-desktop-portal-gtk`

### Required, may not come from third parties:

#### Settings application

### Optional, but bundled with almost every installation

> **NOTE:** For this section, we want to choose the most self-contained options out there. We don't want for example a file manager that pulls in half of another desktop environment in order to have all its functionality. Rust-based solutions will hopefully excel in being self-contained.

#### File Manager

#### Terminal Emulator

#### App Store

