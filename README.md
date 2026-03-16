# macos-darkmode

> Fork of [mafredri/macos-darkmode](https://github.com/mafredri/macos-darkmode) with a fix for building on modern macOS (arm64), where `BOOL` is C99 `_Bool` instead of `signed char`.

Your friendly neighborhood macOS Dark Mode CLI. Dark Mode is set via Apples private APIs instead of the usual Apple Script.

Tested on macOS Mojave (10.14) and macOS Sequoia (15, arm64).

## Installing

```console
$ go build -o darkmode ./cmd/darkmode
$ codesign -s - darkmode
$ cp darkmode /usr/local/bin/
```

The binary must be ad-hoc signed after building, otherwise macOS will kill it when it tries to access the private SkyLight framework.

## Usage

### Get current Dark Mode

```console
$ darkmode
on
```

### Set Dark Mode

```console
$ darkmode on
$ darkmode off
$ darkmode toggle
```

## Why?

Sometimes setting Dark Mode via Apple Script just doesn't work, I wanted a more reliable method.

## See also

- [macos-brightness](https://github.com/mafredri/macos-brightness): Simple CLI for changing brightness on macOS

## Thanks

Thanks to Saagar Jha for discovering the private APIs and sharing them in his post on [Scheduling Dark Mode](https://saagarjha.com/blog/2018/12/01/scheduling-dark-mode/).
