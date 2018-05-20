<h1>Level 11</h1>

<h2>Level Goal</h2>
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

<h2>Solution</h2>


>//

    $ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

>info

    https://en.wikipedia.org/wiki/ROT13
    tr translate or delete characters

>//

      Password: 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu

>//

      $ ssh -p 2220 bandit12@bandit.labs.overthewire.org
