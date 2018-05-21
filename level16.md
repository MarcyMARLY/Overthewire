<h1>Level 16</h1>

<h2>Level Goal</h2>
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

<h2>Solution</h2>


>//

    $ nmap  -p 31000-32000 localhost
      //Found open ports
>output

    Starting Nmap 7.01 ( https://nmap.org ) at 2018-05-20 21:02 CEST
    Nmap scan report for localhost (127.0.0.1)
    Host is up (0.00019s latency).
    Other addresses for localhost (not scanned): ::1
    Not shown: 996 closed ports
    PORT      STATE SERVICE
    31046/tcp open  unknown
    31518/tcp open  unknown
    31691/tcp open  unknown
    31790/tcp open  unknown
    31960/tcp open  unknown
>//

    $ nmap  -p 31000-32000  --script ssl-enum-ciphers localhost
      // Try to find ssl understanding ports.
>output

    Starting Nmap 7.01 ( https://nmap.org ) at 2018-05-20 21:04 CEST
    Nmap scan report for localhost (127.0.0.1)
    Host is up (0.00023s latency).
    Other addresses for localhost (not scanned): ::1
    Not shown: 996 closed ports
    PORT      STATE SERVICE
    31046/tcp open  unknown
    31518/tcp open  unknown
    | ssl-enum-ciphers:
    |   TLSv1.0:
    |     ciphers:
    |       TLS_RSA_WITH_AES_128_CBC_SHA (rsa 2048) - A
    |     compressors:
    |       NULL
    |     cipher preference: indeterminate
    |     cipher preference error: Too few ciphers supported
    |_  least strength: A
    31691/tcp open  unknown
    31790/tcp open  unknown
    | ssl-enum-ciphers:
    |   TLSv1.0:
    |     ciphers:
    |       TLS_RSA_WITH_AES_128_CBC_SHA (rsa 2048) - A
    |     compressors:
    |       NULL
    |     cipher preference: indeterminate
    |     cipher preference error: Too few ciphers supported
    |_  least strength: A
    31960/tcp open  unknown
>//

    $ nmap -sV -p 31000-32000 localhost
      //Anothe way to find ssl understanding ports.
>output

    Starting Nmap 7.01 ( https://nmap.org ) at 2018-05-20 21:06 CEST
    Stats: 0:00:16 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
    Service scan Timing: About 0.00% done
    Nmap scan report for localhost (127.0.0.1)
    Host is up (0.00029s latency).
    Other addresses for localhost (not scanned): ::1
    Not shown: 996 closed ports
    PORT      STATE SERVICE     VERSION
    31046/tcp open  echo
    31518/tcp open  ssl/echo
    31691/tcp open  echo
    31790/tcp open  ssl/unknown
    31960/tcp open  echo
    1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
    SF-Port31790-TCP:V=7.01%T=SSL%I=7%D=5/20%Time=5B01C75C%P=x86_64-pc-linux-g
    SF:nu%r(GenericLines,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20cu
    SF:rrent\x20password\n")%r(GetRequest,31,"Wrong!\x20Please\x20enter\x20the
    SF:\x20correct\x20current\x20password\n")%r(HTTPOptions,31,"Wrong!\x20Plea
    SF:se\x20enter\x20the\x20correct\x20current\x20password\n")%r(RTSPRequest,
    SF:31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20password\
    SF:n")%r(Help,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x
    SF:20password\n")%r(SSLSessionReq,31,"Wrong!\x20Please\x20enter\x20the\x20
    SF:correct\x20current\x20password\n")%r(TLSSessionReq,31,"Wrong!\x20Please
    SF:\x20enter\x20the\x20correct\x20current\x20password\n")%r(Kerberos,31,"W
    SF:rong!\x20Please\x20enter\x20the\x20correct\x20current\x20password\n")%r
    SF:(FourOhFourRequest,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20c
    SF:urrent\x20password\n")%r(LPDString,31,"Wrong!\x20Please\x20enter\x20the
    SF:\x20correct\x20current\x20password\n")%r(SIPOptions,31,"Wrong!\x20Pleas
    SF:e\x20enter\x20the\x20correct\x20current\x20password\n");

    Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
    Nmap done: 1 IP address (1 host up) scanned in 89.22 seconds

>//

    //Here we have two ports working with ssl. We will test both.
    $ openssl s_client -ign_eof -connect localhost:31518
      // This port is just echoed my request.
    $ openssl s_client -ign_eof -connect localhost:31790
      // This returned private key.
>output

    cluFn7wTiGryunymYOu4RcffSxQluehd
    Correct!
    -----BEGIN RSA PRIVATE KEY-----
    MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
    imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
    Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
    DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
    JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
    x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
    KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
    J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
    d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
    YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
    vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
    +TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
    8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
    SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
    HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
    SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
    R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
    Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
    R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
    L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
    blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
    YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
    77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
    dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
    vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
    -----END RSA PRIVATE KEY-----

    closed

>info

    nmap - Network exploration tool and security / port scanner
      -p port ranges (Only scan specified ports) .
        This option specifies which ports you want to scan and overrides the default. Individual port numbers are OK, as are ranges separated by a hyphen (e.g.  1-1023). The beginning and/or end
        values of a range may be omitted, causing Nmap to use 1 and 65535, respectively. So you can specify -p- to scan ports from 1 through 65535. Scanning port zero.  is allowed if you specify it
        explicitly. For IP protocol scanning (-sO), this option specifies the protocol numbers you wish to scan for (0-255).

      nmap with “-sV” option, used to identify services and it is also able to identify SSL services

    openssl - OpenSSL command line tool

      s_client  
        This implements a generic SSL/TLS client which can establish a transparent connection to a remote server speaking SSL/TLS. It's intended for testing purposes only and provides only rudimentary interface functionality but internally uses mostly all functionality of the OpenSSL ssl library.

        -connect host:port - who to connect to (default is localhost:4433)

        -ign_eof      - ignore input eof (default when -quiet)


>//

    $ atom sshkey.private
    $ chmod 600 sshkey.private
    $ ssh -p 2220 bandit17@bandit.labs.overthewire.org -i sshkey.private
    
