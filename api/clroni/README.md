# clroepcie 
CLR/.NET bindings for [`liboni`](../liboni/README.md).

## Build

### Visual Studio (Windows)
1. Open the `clroni.sln` solution in visual studio. 
2. "Running" the solution will compile the library and test program, and then
   run the test program

__Notes (aka please help...)__

- I removed the Any CPU build option because I don't understand how to use it
  properly. Instead, I build two times for each x64 and x86
- Each build type has a post build event in which the liboni.dll (of
  appropriate architecture) is copied from the Externals folder to the target
  directory so that it will be included in the nuget package.

__Creating the nuget package__
```
nuget pack clroni.csproj -properties Configuration=Release
```

### Mono
[Mono](https://github.com/mono/mono) is an open source .NET implementation.
`mcs` is the mono C# compiler.

```
$ cd clroepcie
$ make
```

## Test Programs
The [clroepcie-test](clroni-test) directory contains minimal working
programs that use this library

1. `Host.exe` : Basic data acquisition loop. Communicate with
   `liboni-test/firmware` or actual hardware.

This will be automatically built when the visual studio solution is built. It
can also be built using mono via

```
$ cd clroni-test
$ make
```

## License
[MIT](https://en.wikipedia.org/wiki/MIT_License)
