# Level 0 -> Level 1
Solution: ssh bandit0@bandit.labs.overthewire.org -p 2220

# Level 1 -> Level 2
Solution: 
```
cat ./-
```

Explanation: We need to use relative path because the command line reads the "-" character as a command option.

# Level 2 -> Level 3
Solution: 
```
cat ./--spaces\ in\ this\ filename--
```

Explanation: The backslash in the command line is used, among other things, to escape spaces.

# Level 3 -> Level 4
Solution: 
```
ls -a
```

Explanation: Command ls with -a option shows hidden files.

# Level 4 -> Level 5
Solution:
```
file inhere/*
```
             
Explanation: File command will print type of data in each file. Only one (-file07) which have "ASCII text" type is readable.
