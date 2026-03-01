# Level 10 -> Level 11
Solution:
```
base64 -d data.txt
```

# Level 11 -> Level 12
Solution:
```
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

Explanation: The ROT13 cipher is a cipher that shifts letters 13 positions. This must be reversed by mapping the letters with the tr command. What is visible in the tr command is just a shorthand. For example, A-Z will ultimately be transmitted as any letter from a to z.

# Level 12 -> Level 13
Solution:

#### First step:
```
mktemp -d
cd /tmp/tmp.bmjbA4zYd
xxd -r /home/bandit12/data.txt data
```

#### Second step (if it's gzip file after check):
```
file data
mv data data.gz
gunzip data.gz
```

#### Alternatives for tar and bzip2:
```
mv data data.bz2
bunzip2 data.bz2
```

```
mv data data.tar
tar -xf data.tar
```

Explanation: The file needs to be translated from the hexdump using xxd. It's best to immediately move it somewhere you have permissions, in this case to the directory created by mktemp -d (its name will always be random!). The file is compressed multiple times using various programs. You need to check which one to use with the file command and change the extension using mv. Finally, after unpacking it several times, you get a text file with the password included.

# Level 13 -> Level 14
Solution (USING HOST TERMINAL!):
```
scp -P 2220 bandit13@bandit.labs.overthewire.org:/home/bandit13/sshkey.private /home/username/Dokumenty
chmod 600 /home/username/Dokumenty/sshkey.private
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
cat /etc/bandit_pass/bandit14
```

Explanation: I don't know if this was the case before, but it's currently impossible to log in from an active SSH connection to another one. Furthermore, the sshkey.private file located on the bandit13 user's disk requires privileges that can't be elevated from their account. Therefore, we need to copy the file to our host's local disk using the scp command. Then we change the file permissions and log in via SSH with the -i option, passing our file as an argument.

# Level 14 -> Level 15
Solution:
```
nc localhost 30000
```

