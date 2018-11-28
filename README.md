# gpick-flatpak

**Gpick** is an advanced color picker and palette editing tool.

![gpick-flatpak screenshot](gpick-flatpak.png)

[Homepage](http://www.gpick.org)

This repo is about the flatpak package.

## Instructions

### Requirements

* [flatpak](https://github.com/flatpak/flatpak)
* [flatpak-builder](https://github.com/flatpak/flatpak-builder)

For EL7:

```
# yum install 'flatpak' 'flatpak-builder'
```

You may also wish to install the `xdg-desktop-portal*` packages:

```
# yum install 'xdg-desktop-portal*'
```

See also:

* [flatpak setup](https://flatpak.org/setup)

### Adding repository

```
$ flatpak remote-add --if-not-exists "flathub" "https://dl.flathub.org/repo/flathub.flatpakrepo"
```

See also:

* [flathub setup](http://docs.flatpak.org/en/latest/using-flatpak.html#add-a-remote)

### Prepare

```
$ flatpak install "flathub" "org.freedesktop.Sdk//18.08"
```

```
$ flatpak install "flathub" "org.freedesktop.Platform//18.08"
```

```
$ git submodule init
```

```
$ git submodule update
```

### Build

```
$ mkdir -p "build" && flatpak-builder "build" "com.github.thezbyg.gpick.yaml" --force-clean --install-deps-from="flathub"
```

### Test

```
$ flatpak-builder --run "build" "com.github.thezbyg.gpick.yaml" "sh"
```

### Test run

```
$ flatpak-builder --run "build" "com.github.thezbyg.gpick.yaml" "gpick"
```

### Install

```
$ flatpak-builder --repo="repo" --force-clean "build" "com.github.thezbyg.gpick.yaml"
```

```
$ flatpak --user remote-add --no-gpg-verify "gpick" "repo"
```

```
$ flatpak --user install "gpick" "com.github.thezbyg.gpick"
```

### Run

```
$ flatpak run "com.github.thezbyg.gpick"
```

### Uninstall

```
$ flatpak --user uninstall "com.github.thezbyg.gpick"
```

```
$ flatpak --user remote-delete "gpick"
```

See also: [Building your first Flatpak](http://docs.flatpak.org/en/latest/first-build.html)

## FAQ

### Does flatpak-ed Gpick run as superuser?

[No](https://github.com/flatpak/flatpak/issues/1557). It is a [MATE](https://github.com/mate-desktop)/[marco](https://github.com/mate-desktop/marco) [issue](https://github.com/mate-desktop/marco/issues/301).

### Why not use an RPM package?

I already provided [COPR repo](https://copr.fedorainfracloud.org/coprs/scx/gpick) with (S)RPM packages for EL.

### Are you the author of Gpick?

No, I only created the flatpak package for it.

See also:

* [GitHub repo](https://github.com/thezbyg/gpick)

