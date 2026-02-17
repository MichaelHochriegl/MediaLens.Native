# MediaLens.Native

**MediaLens.Native** packages the official native binaries of **MediaInfoLib** for consumption in .NET projects.  
This package contains only native libraries (no managed API). For the managed wrapper, use **MediaLens**.

## Install
Install the native package (usually pulled in by the wrapper):

    dotnet add package MediaLens.Native

For the [managed wrapper](https://github.com/MichaelHochriegl/MediaLens) (coming soon):

    dotnet add package MediaLens

## What’s inside
The NuGet package places platform binaries under the standard runtime layout:

    runtimes/
      win-x64/native/MediaInfo.dll
      linux-x64/native/libmediainfo.so
      osx-x64/native/libmediainfo.dylib

Also included in the package: `README.md`, `LICENSE` (MIT), and `LICENSE.MediaInfo` (BSD-2-Clause).

## CI / Publishing
The repository includes a GitHub Actions workflow that:
1. Builds MediaInfoLib for Windows, Linux, macOS.
2. Assembles binaries into `src/MediaLens.Native/runtimes/.../native/`.
3. Packs and publishes the NuGet package on release.

## License & attribution
- **This repository and packaging code**: MIT (`LICENSE`).
- **MediaInfoLib (bundled native binaries)**: BSD-2-Clause (`LICENSE.MediaInfo`), included in the package.

Include and preserve `LICENSE.MediaInfo` when redistributing the binaries.

---
