# Level 5 -> Level 6
Solution 1 (works): 
```
find inhere -size 1033c
```

Solution 2 (appropriate - matching requirements): 
```
find inhere -size 1033c \! -executable -exec file {} + | grep "ASCII text"
```

Explanation: Using the first solution is sufficient, as there are no other files of this size in this directory. However, assuming there are more, the second solution should be used, which searches for these files according to the specified requirements. The find command does not have an option to check whether a file is human-readable (not to be confused with the -readable option, which indicates files we are authorized to read). Therefore, we must also invoke the file command using -exec. The -exec command passes the output of the preceding command to its argument. The file path is enclosed in curly braces ("{ }"), and the "+" indicates that find must first find all files before passing them to the file command. The most common alternative to "+" is "/." In this configuration, find will call file for each file found.

# Level 6 -> Level 7
Solution: 
```
find / -size 33c -type f -user bandit7 -group bandit6 2>/dev/null
```

Explanation: We start at the root directory (/), with options as required. 2>/dev/null means forwarding stderr stream to /dev/null which is used for junk informations cleaning. System will inform that writing to the file was succesfull, but the data are actually deleted. 

# Level 7 -> Level 8
Solution:
```
grep -i 'millionth' data.txt
```

# Level 8 -> Level 9
Solution:
```
sort -R data.txt | uniq -u
```

# Level 9 -> Level 10
Solution:
```
strings data.txt | grep -E '={2,}'
```

Explanation: The -E option in the grep command means to interpret search patterns as "extended regular expressions". More about their structures: https://en.wikibooks.org/wiki/Regular_Expressions/POSIX-Extended_Regular_Expressions
