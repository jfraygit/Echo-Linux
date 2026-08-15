# EchoMix for Linux — test repository

This is the Dalamud plugin repository for the **Linux build** of [EchoMix](https://echoxiv.com).

It talks to the same relay as the normal Windows build, so your DJ profile, your followers and every
live show are exactly the same — you'll see the same people and they'll see you. The difference is
under the hood: the audio engine is a native Linux program using PipeWire/PulseAudio, instead of the
Windows one running through Wine's emulated audio.

## Install

Add this URL in Dalamud under **Settings → Experimental → Custom Plugin Repositories**:

```
https://raw.githubusercontent.com/jfraygit/Echo-Linux/main/pluginmaster.json
```

Then install **EchoMix (Linux)** from the plugin installer.

It installs as a **separate plugin** from the normal EchoMix, so it won't disturb or replace an
existing install — you can have both and remove this one at any time. The trade-off is that it
starts with its own empty playlists and sound pads. Your DJ profile, followers and shows are stored
on the relay, so those carry across untouched.

## Requirements

Almost nothing — the plugin brings its own runtime, and mp3, flac, wav and ogg all play with no
extra software.

| | Needed? | If missing |
|---|---|---|
| **libpulse** | Yes | No audio at all. Already present on any Linux desktop with working sound. |
| **PipeWire tools** | Optional | Spotify Mode captures your whole audio output instead of just Spotify — so anything else making noise goes out to your listeners. |
| **ffmpeg** | Optional | aac, m4a and wma files won't play. Everything else is unaffected. |

## If something isn't working

The plugin ships with a self-check. Run it from a terminal — it reports exactly what your machine
can and can't do, and which relay the build is pointed at:

```sh
~/.xlcore/installedPlugins/EchoMixLinux.Plugin/*/AudioHost/EchoMix.AudioHost --check
```

A healthy machine reports `Ready.` There's also a setup script in the plugin folder that can install
anything missing:

```sh
~/.xlcore/installedPlugins/EchoMixLinux.Plugin/*/echomix-linux-setup.sh            # just report
~/.xlcore/installedPlugins/EchoMixLinux.Plugin/*/echomix-linux-setup.sh --install  # fix it
```

## This is a test build

It's had a lot of verification off the game — audio playback, decoding, the relay connection,
hosting and joining shows — but the part that hands off between Wine and the native binary can only
really be exercised in a live game, which is what this repository is for.

Worth reporting if you hit it:

- EchoMix not starting at all, or the window opening with no audio
- Anything in the plugin's own **Report Bug** button, which attaches the log automatically
- Spotify Mode or External Input Mode behaving differently to what you're used to
