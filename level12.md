<h1>Level 12</h1>

<h2>Level Goal</h2>
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

<h2>Solution</h2>


>//

    $ cd ../../tmp
    $ mkdir testMariyam
    $ cp ../../home/bandit12/data.txt .
    $ xxd -r data.txt > data1
    $ file data1
>output

    data1: gzip compressed data, was "data2.bin", last modified: Thu Dec 28 13:34:36 2017, max compression, from Unix
>//

    $ mv data1 data1.gz
    $ gzip -d data1.gz
    $ file data1
>output

    data1: bzip2 compressed data, block size = 900k

>//

    $ bzip2  -d data1
    $ file data1.out
>output

    data1.out: gzip compressed data, was "data4.bin", last modified: Thu Dec 28 13:34:36 2017, max compression, from Unix

>//

    $ mv data1.out data1.out.gz
    $ gzip -d data1.out.gz
    $ file data1.out
>output

    data1.out: POSIX tar archive (GNU)
>//

    $ tar xvf data1.out
    $ file data5.bin
>output

    data5.bin: POSIX tar archive (GNU)

>//

    $ tar xvf data5.bin
    $ file data6.bin
>output

    data6.bin: bzip2 compressed data, block size = 900k
>//

    $ bzip2 -d data6.bin
    $ file data6.bin.out
>output

    data6.bin.out: POSIX tar archive (GNU)
>//

    $ tar xvf data6.bin.out
    $ file data8.bin
>output

    data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Dec 28 13:34:36 2017, max compression, from Unix
>//

    $ mv data8.bin data8.bin.gz
    $ gzip -d data8.bin.gz
    $ file data8.bin
>output

    data8.bin: ASCII text
>//

    $ cat data8.bin

>info

    xxd - make a hexdump or do the reverse.
        -r | -revert
                reverse  operation: convert (or patch) hexdump into binary.  If not writing to stdout, xxd writes into its output file without truncating it. Use the combination -r -p to read plain hexadecimal
                dumps without line number information and without a particular column layout. Additional Whitespace and line-breaks are allowed anywhere.
    file -- determine file type
    gzip, gunzip, zcat - compress or expand files
      -d --decompress --uncompress
              Decompress.
    bzip2, bunzip2 - a block-sorting file compressor, v1.0.6
       bzcat - decompresses files to stdout
       bzip2recover - recovers data from damaged bzip2 files

       -d --decompress
                 Force decompression.  bzip2, bunzip2 and bzcat are really the same program, and the decision about what actions to take is done on the basis of which name is used.   This  flag  overrides  that
                 mechanism, and forces bzip2 to decompress.



>//

      Password: 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL

>//

      $ ssh -p 2220 bandit13@bandit.labs.overthewire.org
