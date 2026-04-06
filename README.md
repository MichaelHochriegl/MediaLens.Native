[![.NET](https://img.shields.io/badge/.NET-10.0-512BD4?logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/)
[![NuGet](https://img.shields.io/nuget/v/MediaLens.Native)](https://www.nuget.org/packages/MediaLens.Native/)
[![MediaInfo version](https://img.shields.io/badge/dynamic/json?label=MediaInfo%20version&query=%24.version&url=https://raw.githubusercontent.com/MichaelHochriegl/MediaLens.Native/main/mediainfo-version.json)](https://mediaarea.net/en/MediaInfo)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![CI](https://github.com/MichaelHochriegl/MediaLens.Native/actions/workflows/cicd.yml/badge.svg)](https://github.com/MichaelHochriegl/MediaLens.Native/actions/workflows/cicd.yml)

# MediaLens.Native

MediaLens.Native packages the official native binaries of [MediaInfoLib](https://mediaarea.net/en/MediaInfo) for use in .NET projects.  
It contains only native libraries, with no managed API. For the managed wrapper, use [MediaLens](https://github.com/MichaelHochriegl/MediaLens).

## Features

- official MediaInfoLib native binaries
- NuGet-friendly runtime layout
- ready to use from managed .NET applications
- included license files for redistribution

## Supported platforms
- Windows x64
- Linux x64
- macOS x64
- macOS ARM64

## Installation

```bash
dotnet add package MediaLens.Native
```

The managed wrapper can be added separately when needed:

```bash
dotnet add package MediaLens
```

## What's inside

The NuGet package places platform binaries under the standard runtime layout:

```text
runtimes/
  win-x64/native/MediaInfo.dll
  linux-x64/native/libmediainfo.so
  osx-x64/native/libmediainfo.dylib
  osx-arm64/native/libmediainfo.dylib
```

The package also includes:

- `README.md`
- `LICENSE` (MIT)
- `LICENSE.MediaInfo` (BSD-2-Clause)

## Usage

`MediaLens.Native` is usually consumed indirectly through the managed wrapper [MediaLens](https://github.com/MichaelHochriegl/MediaLens).  
If you reference it directly, make sure your application can resolve the native libraries from the package runtime assets.

## CI / Publishing

The repository includes a GitHub Actions workflow that:

1. builds MediaInfoLib for Windows, Linux, and macOS
2. assembles binaries into `src/MediaLens.Native/runtimes/.../native/`
3. packs and publishes the NuGet package on release

## License

- **This repository and packaging code**: MIT (`LICENSE`)
- **MediaInfoLib bundled native binaries**: BSD-2-Clause (`LICENSE.MediaInfo`)

Please include and preserve `LICENSE.MediaInfo` when redistributing the binaries.
