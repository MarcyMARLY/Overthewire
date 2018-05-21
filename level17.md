<h1>Level 17</h1>

<h2>Level Goal</h2>
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19
<h2>Solution</h2>


>//

    $ diff passwords.new passwords.old

>output

    42c42
    < kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
    ---
    > 6vcSC74ROI95NqkKaeEC2ABVMDX9TyUr


>//

      Password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd

>//

      $ ssh -p 2220 bandit18@bandit.labs.overthewire.org
