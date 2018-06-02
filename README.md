MINIGEN: Small utility for minixsf creation assistance
======================================================
[![Travis Build Status](https://travis-ci.org/loveemu/minigen.svg?branch=master)](https://travis-ci.org/loveemu/minigen) [![AppVeyor Build Status](https://ci.appveyor.com/api/projects/status/qr3a767i6pr975bw/branch/master?svg=true)](https://ci.appveyor.com/project/loveemu/minigen/branch/master)

Minigen is a small binary file creation utility for numbered custom minipsf blocks.

Usage
-----

Syntax: `minigen [out basename] [file count] [hex string]`

Minigen will produce the number of files that has been specified by file count.
The file content is determined by hex string. In the string, you can embed a single special symbol NN, which will be expanded to little-endian integer.

Example of output:

```
C:\> minigen gametitle 4 NNNNNNNNa0380408
Created gametitle-0000.bin => 00000000a0380408
Created gametitle-0001.bin => 01000000a0380408
Created gametitle-0002.bin => 02000000a0380408
Created gametitle-0003.bin => 03000000a0380408
```

To convert them to minixsf, you will need a proper converter,
such as rom2snsf or rom2gsf (embedded in saptapper).

```
C:\> for %a in (*.bin) do saptapper --rom2gsf --lib gametitle.snsflib --load 0x80b1248 --psfby laala "%a"
```
