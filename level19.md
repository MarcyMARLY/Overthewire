<h1>Level 19</h1>

<h2>Level Goal</h2>
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

<h2>Solution</h2>


>//

    $ ./bandit20-do
    $ ./bandit20-do cat ../../etc/bandit_pass/bandit20


>//

      Password: GbKksEFF4yrVs6il55v6gwY5aVje5f0j

>//

      $ ssh -p 2220 bandit20@bandit.labs.overthewire.org
