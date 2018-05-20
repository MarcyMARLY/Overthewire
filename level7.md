<h1>Level 7</h1>

<h2>Level Goal</h2>
The password for the next level is stored in the file data.txt next to the word millionth

<h2>Solution</h2>


>//

    $ strings data.txt |grep millionth

>output

    millionth	cvX2JJa4CFALtqS87jk27qwqGhBM9plV

>info

    strings - print the strings of printable characters in files.

>//

      Password: cvX2JJa4CFALtqS87jk27qwqGhBM9plV

>//

      $ ssh -p 2220 bandit8@bandit.labs.overthewire.org
