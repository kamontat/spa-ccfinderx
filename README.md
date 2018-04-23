# spa-ccfinderx
result of searching duplicate code in (https://github.com/lz4/lz4)

## More about lz4


> LZ4 is lossless compression algorithm, providing compression speed at 400 MB/s per core, scalable with multi-cores CPU. It features an extremely fast decoder, with speed in multiple GB/s per core, typically reaching RAM speed limits on multi-core systems.


Use [ccfinderX](https://github.com/petersenna/ccfinderx-core) to finding duplicate code in project ([lz4](https://github.com/lz4/lz4))

# Files

1. [ccfinderx.out](./ccfinderx.out) is output of `./ccfx/ccfx p` command
2. [ccfinderx.xml](./ccfinderx.xml) is formatting output (.out) to .xml file
3. [dups](./dups) make a list of files that are likely to be very similar

# Metrics

1. [file-metrics](./file-matrics.csv) is calculation of file metrics
2. [clone-metrics](./clone-matrics.csv) is calculation of clone metrics
3. [line-metrics](./line-matrics.csv) is calculation of line metrics

## Explaination

1. File Metrics
  - `NBR` (neighbor):	Count of files that have a code-clone fragment between the file.
  - `RSA` (ratio of similarity between another files): Ratio (percentage) of tokens that are covered by a code clone between the file and one of the other files. If a file has a RSA value close to 100%, then it is possible that the file was created by copying a file.
  - `RSI` (ratio of similarity within the file): Ratio (percentage) of tokens that are covered by a code clone enclosed within the file. If a file has a RSI value close to 100%, then it is possible that the file contains a series of the similar functions or methods.
  - `CVR` (coverage):	Ratio (percentage) of tokens that are covered by any code clone. By definition, max(RSA, RSI) <= CVR <= RSA+RSI
  - `RNR` (ratio of non-repeated code): Ratio of non-repeated code. 1 - (ratio of tokens appears in repetition in the text) If the value is near to zero, the code is repetition of simple statements and/or defenitions.
2. Clone Metrics
  - `LEN` (length):	Length (in token) of a code fragment of the code clone
  - `POP` (population): Count of code fragments of the code clone
  - `NIF`: Count of source files that include one or more code fragments of the code clone. By definition, NIF <= POP (This metric is imported from Gemini, developed by Yoshiki Higo, Osaka Univ..)
  - `RAD` (radius):	Range of the source code fragments of a code clone in the directory hierarchy. (When all the code fragments of the code clone are located in one source file, the value is 0.)
  - `RNR` (ratio of non-repeated tokens): Ratio (percentage) of tokens that are not included in repeated part of a code fragment of the code clone.
  - `TKS` (token set size): Size of a set of tokens of a code fragment of the code clone. If a code clone has a extremely small TKS value, then the code fragment is a simple statement, such as a series of declaration of variables.
  - `LOOP`: defined as count of loops in a code fragment, 
  - `COND`: defined as count of conditional branches
  - `McCabe`: defined as the sum of them. In order to focus attention on complex code, select code clones with the higher values of these metrics.
3. Line Metrics
  - `LOC`:	Raw line count of the soure file.
  - `SLOC`:	Count of lines, in case of excluding lines whithout any valid tokens. Here, the "tokens" are specific to CCFinderX. (For example, definitions of simple getters/setters in Java source file will be entirely neglected by CCFinderX.) Such neglected characters are shown in green color in Source Text view.
  - `CLOC`:	Count of lines including at least one token of a code fragment of a code clone.
  - `CVRL`:	Ratio of the lines including a token of a code fragment of a code clone. CVRL = CLOC / SLOC.
