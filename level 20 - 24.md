# Level 20 -> Level 21
Solution: 
#### First step:
```
tmux new -s session_name
```
or just
```
tmux 
```
Use ctrl + b and % to vertical split terminal screen.

#### In first window:
```
nc -lk 60000
```
Paste there password, even just after listening started.
#### In second window:
````
./suconnect
````
If password was pasted before, it will send back next password to the first window right away.

Explanation: You don't have listen to port 60000, any other free port will be ok. It can be checked for example with nmap -p<port>-<port>.

# Level 21 -> Level 22
Solution:
```
cat /tmp t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
Explanation: The file in the /etc/cron.d directory specifies the cyclic execution of the cronjob_bandit22.sh script in the /usr/bin location. Opening it reveals that it grants permissions to a file in the /tmp directory and assigns the password to the next level of the same file. Display the contents of this file using the cat command.

# Level 22 -> Level 23
Solution:
```
echo I am user bandit23 | md5sum | cut -d ' ' -f 1
```
The result must be copied to the cat command.
```
cat /tmp/8ca319486bfbbc3663ea0fbe81326349
```

Explanation: Generally, it all comes down to figuring out that the script in /usr/bin/cronjob_bandit23.sh reads the name of the current user, i.e. bandit22, and we want to get the password for 23.

# Level 23 -> Level 24


