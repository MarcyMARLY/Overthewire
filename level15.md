<h1>Level 15</h1>

<h2>Level Goal</h2>
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

<h2>Solution</h2>


>//

    $ cd ../../etc/bandit_pass/
    $ cat bandit15
    $ openssl s_client -ign_eof -connect localhost:30001
      After port info you should enter the password.

>info

    openssl - OpenSSL command line tool
    
      s_client  
        This implements a generic SSL/TLS client which can establish a transparent connection to a remote server speaking SSL/TLS. It's intended for testing purposes only and provides only rudimentary interface functionality but internally uses mostly all functionality of the OpenSSL ssl library.

        -connect host:port - who to connect to (default is localhost:4433)

        -ign_eof      - ignore input eof (default when -quiet)


>//

      Password: cluFn7wTiGryunymYOu4RcffSxQluehd

>//

      $ ssh -p 2220 bandit16@bandit.labs.overthewire.org
