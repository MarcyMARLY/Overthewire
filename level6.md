<h1>Level 6</h1>

<h2>Level Goal</h2>
The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7
owned by group bandit6
33 bytes in size

<h2>Solution</h2>

>//

    $ find / -user bandit7 -group bandit6 -size 33c

>output

    find: '/var/log': Permission denied
    find: '/var/lib/puppet': Permission denied
    find: '/var/lib/apt/lists/partial': Permission denied
    /var/lib/dpkg/info/bandit7.password
    find: '/var/lib/polkit-1': Permission denied
    find: '/var/spool/rsyslog': Permission denied
    find: '/var/spool/bandit24': Permission denied
    find: '/var/spool/cron/atspool': Permission denied
    find: '/var/spool/cron/atjobs': Permission denied
    find: '/var/spool/cron/crontabs': Permission denied
    find: '/var/crash': Permission denied

>//

      $ cat /var/lib/dpkg/info/bandit7.password

>//

      Password: HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

>//

      $ ssh -p 2220 bandit7@bandit.labs.overthewire.org
