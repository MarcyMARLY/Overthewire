<h1>Level 9</h1>

<h2>Level Goal</h2>
The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several ‘=’ characters.

<h2>Solution</h2>


>//

    $ strings data.txt | grep "="
>output

    nfZ=
    U=R*q
    =-VW+
    ========== theP`
    	=uN
    P5J7=^
    ========== password
    L='.
    L========== isA
    G&eB_=
    9T=8?
    9=!/"
    ========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

>info

    strings commands finds all the human-readable strings within a file.

>//

      Password: truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

>//

      $ ssh -p 2220 bandit10@bandit.labs.overthewire.org
