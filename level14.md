<h1>Level 14</h1>

<h2>Level Goal</h2>
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

<h2>Solution</h2>


>//

    $ cd ../../etc/bandit_pass/
    $ cat bandit14
    $ echo 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e | nc localhost 30000

>info

    nc -- arbitrary TCP and UDP connections and listens

>//

      Password: BfMYroe26WYalil77FoDi9qh59eK5xNr

>//

      $ ssh -p 2220 bandit15@bandit.labs.overthewire.org
