<h1>Level 4</h1>

<h2>Level Goal</h2>
The password for the next level is stored in the only human-readable file in the inhere directory.
Tip: if your terminal is messed up, try the “reset” command.

<h2>Solution</h2>

  > $ ls
  > $ cd inhere/
  > $ find . -type f -exec file {} + 

    -type c
               File is of type c:

               b      block (buffered) special

               c      character (unbuffered) special

               d      directory

               p      named pipe (FIFO)

               f      regular file

               l      symbolic link; this is never true if the -L option or the
                      -follow option is in effect, unless the symbolic link  is
                      broken.  If you want to search for symbolic links when -L
                      is in effect, use -xtype.

               s      socket

               D      door (Solaris)
    -exec command {} +
                This  variant  of the -exec action runs the specified command on
                the selected files, but the command line is built  by  appending
                each  selected  file  name  at  the  end;  the  total  number of
                invocations of the command will be much less than the number  of
                matched  files.   The command line is built in much the same way
                that xargs builds its command lines.  Only one instance of  `{}'
                is  allowed  within the command.  The command is executed in the
                starting directory.  If  find  encounters  an  error,  this  can
                sometimes  cause an immediate exit, so some pending commands may
                not be run at all.  This variant of -exec always returns true.

<code>
./-file08: data <br/>
./-file06: data <br/>
./-file02: data <br/>
./-file07: ASCII text <br/>
./-file05: data <br/>
./-file09: data <br/>
./-file04: data <br/>
./-file03: data <br/>
./-file00: data <br>
./-file01: data <br/>
</code>
