# wignix-installer

The WigNix installer: a menu-driven installer for the WigNix repository.

A fork of the Void Linux installer by Juan Romero Pardines and Dave
Elusive, adapted for WigNix. It installs from the live disc's rootfs.

## What the WigNix changes do

- **No network step.** The target always gets `dhcpcd` enabled, and when a
  wireless interface exists the live `wpa_supplicant.conf` is copied over
  and `wpa_supplicant` enabled, so a connection set up on the live desktop
  carries into the installed system.
- **Machine packages from the rootfs.** The machine packages are read from
  `/usr/share/wignix/repo` inside the rootfs, so the installer finds them
  even on a RAM boot where the disc is no longer mounted.
- **Headless installs.** The `/etc/wignix-headless` marker enables `sshd`
  and leaves `slim` out of the target.
- **AIDE reports** go to `/root/aide/aide-report-<date>.txt`.

## Files

| file | what |
| --- | --- |
| `wignix-installer` | the installer (bash, dialog-driven) |
| `COPYING` | the BSD 2-Clause licence text |

## Installing

The installer runs from the live disc. It writes `@@MKLIVE_VERSION@@` into
its version at package time; the template does that substitution.

The xbps-src template that packages it is `srcpkgs/wignix-installer` in
`wignix-packages`.

## License

BSD 2-Clause. The copyright notice of the original Void installer is kept
in the source and in `COPYING`.
