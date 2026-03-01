# Level 15 -> Level 16
Solution:
```
openssl s_client -connect localhost:30001
```

# Level 16 -> Level 17
Solution:
```
openssl s_client -quiet -connect localhost:31790
```

Explanation: Without the -quiet option, I got the "KEYUPDATE" message. I couldn't find the password for the next level, because we only get the sshkey (the procedure is the same as between tasks 13 and 14). It might be hidden somewhere in level 17. I didn't spend much time looking.

# Level 17 -> Level 18
Solution:
```
diff passwords.old passwords.new
```

# Level 18 -> Level 19
Solution (IN HOST TERMINAL!):
```
scp -P 2220 bandit18@bandit.labs.overthewire.org:/home/bandit18/readme /home/username/Dokumenty
```

# Level 19 -> Level 20
Solution: 
```
/bandit20-do cat /etc/bandit_pass/bandit20
```

Explanation: Before the cat command, you must include the path to the setuid file. This will grant the appropriate permissions to read the file.
