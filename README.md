# UE4support
Support Package for building Unreal Engine 4 on Win64

## Brief
This is to be used to meet the build dependencies of Unreal Engine 4 on Win64. \
The process is detailed here: https://github.com/UnrealEngineHTML5/Documentation \
It requires that you have linked your Epic Games Account to your Github Account.

![UE4-HTML5](https://github.com/TheMindVirus/UE4support/blob/main/UE4-HTML5.png)

## Additional Dependencies
Further to the sample emsdk packages provided here, Microsoft.NET v4.6.2 Developer Pack \
is also required from here: https://dotnet.microsoft.com/download/dotnet-framework/net462

The branch that this has been tested on includes the scrapped HTML5 Platform Extension (4.24.3-html5-1.39.18) \
which provides a new target platform for running projects directly in a WebGL-compatible browser.

## Notes
EMSDK is yet another command-line in-tree package manager built on python and is part of \
Emscripten - a bridge between Javascript in the browser and C/C++/C# apps (interface to WebAssembly .wasm)

A few files in emsdk may also need patching to remove the (potentially harmful) check for python: \
https://github.com/emscripten-core/emsdk/blob/main/emsdk \
Wherever you see a file doing deliberate version checking, it may need to be commented out entirely \
and replaced with a more accurate last line calling emsdk.py or the relevant build script.

Deliberate version checks and behaviours based on software of a specific version can be \
difficult to maintain further down the development cycle. Sometimes this is the desired behaviour, \
but it can also be written to work with any version of the tools (e.g. "python" instead of "python3.7.4-64bit").

The build process uses about 25GB committed System Memory, so at least 16GB of RAM and a 16GB pagefile \
is necessary to avoid compiler heap size limits. The built solution file opens in Microsoft Blend for Visual Studio.

I recommend a 64GB pagefile if you can as it lets you build the engine while still performing other tasks. \
The unbuilt source files total around 66GB and the process tears through storage, so make sure you have 1TB to spare.

Many errors involving missing environment variables and imports may occur, so be sure to set your `%PATH%`, `%TEMP_DIR%` etc. \
and also install the emscripten python module in site-packages to avoid seeing `import emscripten - no module named 'emscripten'`.

Hopefully this will help you successfully build Unreal Engine 4 and perhaps improve Unreal Engine 5.
