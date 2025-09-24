# MediaLens.Native

**MediaLens.Native** packages the official native binaries of **MediaInfoLib** for consumption in .NET projects.  
This package contains only native libraries (no managed API). For the managed wrapper, use **MediaLens**.

## Install
Install the native package (usually pulled in by the wrapper):

    dotnet add package MediaLens.Native

For the managed wrapper:

    dotnet add package MediaLens

## What’s inside
The NuGet package places platform binaries under the standard runtime layout:

    runtimes/
      win-x64/native/MediaInfo.dll
      linux-x64/native/libmediainfo.so
      osx-x64/native/libmediainfo.dylib

Also included in the package: `README.md`, `LICENSE` (MIT), and `LICENSE.MediaInfo` (BSD-2-Clause).

## Quick build notes
**Linux / macOS (autotools)**
- Clone upstream and build the GNU library:

  git clone https://github.com/MediaArea/MediaInfoLib.git
  cd MediaInfoLib/Project/GNU/Library
  ./autogen.sh
  ./configure --enable-shared
  make -j$(nproc || sysctl -n hw.ncpu)

- Copy the produced `.so` / `.dylib` into `src/MediaLens.Native/runtimes/<rid>/native/`.

**Windows (MSVC)**
- Build the MSVC solution (x64 Release), then copy `MediaInfo.dll` to `src/MediaLens.Native/runtimes/win-x64/native/`:

  msbuild MediaInfoLib\Project\MSVC2019\MediaInfoLib.sln /p:Configuration=Release /p:Platform=x64

## Pack locally
(assumes binaries are already in `src/MediaLens.Native/runtimes/...`)

    dotnet pack src/MediaLens.Native/MediaLens.Native.csproj -c Release -o ./out

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
