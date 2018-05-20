<h1>Level 5</h1>

<h2>Level Goal</h2>
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable

<h2>Solution</h2>
    Human-readable means ASCII text in this case.

    $ ls
    $ cd inhere/
    $ find / -size 1033c ! -executable -type f -exec file {} + | grep ASCII

>output

    /usr/src/linux-headers-4.4.0-98/include/drm/gma_drm.h:                                             ASCII text
    /usr/src/linux-headers-4.4.0-98/arch/arm/include/debug/vf.S:                                       ASCII text
    /usr/src/linux-headers-4.4.0-98/arch/m32r/include/uapi/asm/termios.h:                              C source, ASCII text
    /usr/src/linux-headers-4.4.0-98/arch/powerpc/include/asm/string.h:                                 C source, ASCII text
    /usr/src/linux-headers-4.4.0-116/include/drm/gma_drm.h:                                            ASCII text
    /usr/src/linux-headers-4.4.0-116/arch/arm/include/debug/vf.S:                                      ASCII text
    /usr/src/linux-headers-4.4.0-116/arch/m32r/include/uapi/asm/termios.h:                             C source, ASCII text
    /usr/src/linux-headers-4.4.0-116/arch/powerpc/include/asm/string.h:                                C source, ASCII text
    /usr/src/linux-headers-4.4.0-112/include/drm/gma_drm.h:                                            ASCII text
    /usr/src/linux-headers-4.4.0-112/arch/arm/include/debug/vf.S:                                      ASCII text
    /usr/src/linux-headers-4.4.0-112/arch/m32r/include/uapi/asm/termios.h:                             C source, ASCII text
    /usr/src/linux-headers-4.4.0-112/arch/powerpc/include/asm/string.h:                                C source, ASCII text
    /usr/share/doc/python-pip/reference/pip_download.rst:                                              ASCII text
    /usr/share/vim/vim74/syntax/esmtprc.vim:                                                           ASCII text
    /home/bandit5/inhere/maybehere07/.file2:                                                           ASCII text, with very long lines


>info
    # For more info look level4.md

    -size n[cwbkMG]
              File uses n units of space, rounding up.  The following suffixes can be used:

              `b'    for 512-byte blocks (this is the default if no suffix is used)

              `c'    for bytes

              `w'    for two-byte words

              `k'    for Kilobytes (units of 1024 bytes)

              `M'    for Megabytes (units of 1048576 bytes)

              `G'    for Gigabytes (units of 1073741824 bytes)

              The  size  does  not  count  indirect  blocks, but it does count blocks in sparse files that are not actually allocated.  Bear in mind that the `%k' and `%b' format specifiers of -printf handle
              sparse files differently.  The `b' suffix always denotes 512-byte blocks and never 1 Kilobyte blocks, which is different to the behaviour of -ls.

              The + and - prefixes signify greater than and less than, as usual.  Bear in mind that the size is rounded up to the next unit. Therefore -size -1M is not equivalent  to  -size  -1048576c.   The
              former only matches empty files, the latter matches files from 1 to 1,048,575 bytes.
    -executable
            Matches files which are executable and directories which are searchable (in a file name resolution sense).  This takes into account access control lists and other  permissions  artefacts  which
            the  -perm  test ignores.  This test makes use of the access(2) system call, and so can be fooled by NFS servers which do UID mapping (or root-squashing), since many systems implement access(2)
            in the client's kernel and so cannot make use of the UID mapping information held on the server.  Because this test is based only on the result of the access(2) system call, there is no guaran-
            tee that a file for which this test succeeds can actually be executed.



      $ cat ./maybehere07/.file2

      Password: DXjZPULLxYr17uwoI01bNLQbtFemEgo7


      $ ssh -p 2220 bandit6@bandit.labs.overthewire.org
