# Buildkite Homebrew Formulae

A collection of [Buildkite](https://buildkite.com/) formulae for [Homebrew](http://brew.sh), a package manager for macOS.

To use the formulae, tap this repository into your home brew:

```bash
brew tap buildkite/buildkite
```

This repository will have been cloned into your Homebrew’s `Libray/Taps` directory (most commonly `/usr/local/Homebrew/Library/Taps`), and whenever you do a `brew update` Homebrew will also update this tap (using `git pull`) and you’ll have the latest versions of the formulae.

## buildkite-agent

### Installing

To install [buildkite-agent](https://github.com/buildkite/agent):

```bash
brew install buildkite-agent
```

You then need to configure your agent token, which you can find your agent token on your "Agents" page in Buildkite:

```bash
sed -i '' "s/xxx/INSERT-YOUR-AGENT-TOKEN-HERE/g" "$(brew --prefix)"/etc/buildkite-agent/buildkite-agent.cfg
```

If you want it start on login follow the `brew install` instructions to install the LaunchAgent plist. You’ll also want to make sure your PC is set to automatically login (the agent won’t launch until you've logged in) and you’ve prevented your machine from going to sleep.

Using a LaunchAgent instead of a LaunchDaemon does require a user login, but it allows your tests to use GUI tools (such as the iOS Simulator) and avoids any file permissions problems.

### Upgrading

```bash
brew update && brew upgrade buildkite-agent
```
