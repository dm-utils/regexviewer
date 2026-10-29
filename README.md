# Datamodder Regex Viewer

A Notepad++ plugin that shows what a regular expression does. Paste the
regex the way you got it - on its own, inside Python, JavaScript, C#, Java,
PHP, Go, PowerShell or a sed/grep command, or a whole answer with code
blocks - and every match in the open document is highlighted, each group in
its own colour, with the pattern explained in plain language.

- Match like Notepad++ (default), like the source language, or a fixed
  flavour: Python, JavaScript, .NET, Java, PCRE, POSIX ERE/BRE, RE2
- Converted for Notepad++'s Find, with Replace and Replace all
- Runs on Boost.Regex, the same engine as Notepad++'s own Find

For 64-bit, 32-bit and ARM64 Notepad++. See [src/help.txt](src/help.txt) for usage.

**Website:** [datamodder.com/en/utils/regex-viewer](https://datamodder.com/en/utils/regex-viewer)

## Build

Visual Studio C++ build tools required. Boost.Regex comes in as a git
submodule (`vendor/regex`, pinned to boost-1.89.0), so clone with
`--recursive` (or run `git submodule update --init` in an existing clone):

```
git clone --recursive https://github.com/dm-utils/regexviewer.git
cd regexviewer
build.cmd            compile, close Notepad++, deploy to plugins\RegexViewer, restart
build.cmd nodeploy   compile only (build\RegexViewer.dll)
```

## Release

```
release.cmd
```

Builds `RegexViewer.dll` and zips it with `help.txt` into
`release_staging\RegexViewer.zip` (x64) or `RegexViewer_<arch>.zip`, printing
the SHA-256 the plugin lists need. By default only x64;
`release.cmd x64 x86 arm64` (or the commented line in the script) also builds
the Win32 and ARM64 versions. ARM64 needs the "MSVC C++ ARM64/ARM64EC build
tools" component of Visual Studio.

## Test

```
test.cmd             (test.cmd x86 runs them as a 32-bit program)
```

Golden tests for extracting regexes from pasted code, the explanation,
matching per flavour (with replacements) and the UTF-8 / ANSI position map.

## License

MIT. Boost.Regex is under the Boost Software License.
