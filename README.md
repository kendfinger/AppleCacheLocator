# Apple Cache

This is a reverse engineering attempt of the Apple Content Caching system.

Currently the locator service is implemented, but I am in the process of
writing documentation on how the cache registration and server work.

The goal of this project is to challenge myself in a serious reverse engineering
attempt while also creating something I want to make: an Apple Content Cache that works on Linux servers.

## A Note to Apple

Dear Apple,

I am a good faith actor and due to the design of cache, I do not believe this should cause any harm. Should you consider otherwise, contact me via my email: kaendfinger@gmail.com

Thanks,
Kenneth

## A Note to Users

Please do not abuse the content you see here. I am trying to do this in good faith and do not condone any malicious use of the Apple Content Cache system, whatever that may be.

## Content Caching

Content Caching is available in the Sharing section of System Preferences.
It is used to cache content on your local network for public Apple content or
iCloud content. The `/usr/libexec/AssetCache/AssetCache` is responsible for a majority
of the work. It has an HTTP server that has an API that allows fetching and uploading of content from the server.

## Research

* [Locator Service](locator/README.md)
* [Cache Server API](server/README.md)

## Methodology

The work here was done by using [Charles Proxy](https://www.charlesproxy.com/) and [Frida](https://www.frida.re/).

The `tools/frida-ssl-pin.js` file is a Frida script that can attach to any macOS process and disable all SSL verification and SSL certificate pinning. This has allowed me to deeply examine the requests going to Apple's servers. This script is likely useful
for many other use cases. If anyone else uses it, I'd love to hear about how it was used (I'm a super huge nerd and am quite interested in reverse engineering).
