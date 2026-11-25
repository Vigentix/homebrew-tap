# Vigentix Homebrew Tap

Homebrew casks for apps by Vigentix.

## Osin

An honest, open-source health monitor and cleaner for the macOS menu bar. Source and releases: [Vigentix/osin](https://github.com/Vigentix/osin).

```sh
brew tap vigentix/tap
brew trust vigentix/tap      # recent Homebrew versions ask you to trust third-party taps
brew install --cask osin
```

Osin 0.1 is not notarized yet, so macOS blocks the first launch:

1. Open Osin once and close the warning.
2. Go to **System Settings › Privacy & Security**, scroll down, click **Open Anyway** next to Osin and confirm with your password.

On macOS 15 and later, right-click › Open no longer bypasses this warning. To skip it entirely, remove the quarantine flag:

```sh
xattr -dr com.apple.quarantine /Applications/Osin.app
```

Update or remove:

```sh
brew upgrade --cask osin
brew uninstall --cask osin          # keep settings and history
brew uninstall --zap --cask osin    # also remove settings, history and caches
```

## Updating a cask

After publishing a release, update `version` and `sha256` in `Casks/<name>.rb`:

```sh
shasum -a 256 Osin-<version>.dmg
brew audit --cask --strict vigentix/tap/osin
```
