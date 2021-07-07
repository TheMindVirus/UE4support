# UE4support
Support Package for building Unreal Engine 4 on Win64

This is to be used to meet the build dependencies of Unreal Engine 4 on Win64. \
The process is detailed here: https://github.com/UnrealEngineHTML5/Documentation \
It requires that you have linked your Epic Games Account to your Github Account.

Additional to the emsdk packages provided here, Microsoft.NET v4.6.2 Developer Pack \
is also required from here: https://dotnet.microsoft.com/download/dotnet-framework/net462

EMSDK is yet another command-line in-tree package manager built on python and is part of \
Emscripten - a bridge between Javascript in the browser and C/C++/C# apps (amongst other languages)

A few files in emsdk may also need patching to remove the (potentially harmful) check for python: \
https://github.com/emscripten-core/emsdk/blob/main/emsdk
Wherever you see a file like this, it may need to be commented out entirely and replaced with a \
more accurate last line calling emsdk.py or the relevant build script.

Deliberate version checks and behaviours based on software of a specific version can be \
difficult to maintain further down the development cycle. Sometimes this is the desired behaviour, \
but it can also be written to work with any version of the tools (e.g. "python" instead of "python3.7.4-64bit")

Hopefully this will help you successfully build Unreal Engine 4 and perhaps improve Unreal Engine 5.
