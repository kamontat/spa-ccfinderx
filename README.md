# spa-ccfinderx
result of searching duplicate code in (https://github.com/lz4/lz4)

## More about lz4


> LZ4 is lossless compression algorithm, providing compression speed at 400 MB/s per core, scalable with multi-cores CPU. It features an extremely fast decoder, with speed in multiple GB/s per core, typically reaching RAM speed limits on multi-core systems.


Use [ccfinderX](https://github.com/petersenna/ccfinderx-core) to finding duplicate code in project ([lz4](https://github.com/lz4/lz4))

# Files

1. [ccfinderx.out](./ccfinderx.out) is output of `./ccfx/ccfx p` command
2. [ccfinderx.xml](./ccfinderx.xml) is formatting output (.out) to .xml file
3. [dups](./dups) make a list of files that are likely to be very similar

# Matrics

1. [file-matrics](./file-matrics.csv) is calculation of file metrics
2. [clone-matrics](./clone-matrics.csv) is calculation of clone metrics
3. [line-matrics](./line-matrics.csv) is calculation of line metrics
