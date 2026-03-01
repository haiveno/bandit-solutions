# Level 0 -> Level 1
Solution: ssh bandit0@bandit.labs.overthewire.org -p 2220

# Level 1 -> Level 2
Solution: ```cat ./-```  
Explanation: We need to use relative path because the command line reads the "-" character as a command option.

# Level 2 -> Level 3
Solution: cat ./--spaces\ in\ this\ filename--
Explanation: The backslash in the command line is used, among other things, to escape spaces.

# Level 3 -> Level 4
Solution: ls -a
Explanation: Command ls with -a option shows hidden files.

# Level 4 -> Level 5
Solution: 1. file inhere/*
          2. cat inhere/-file07
Explanation: First command will print type of data in each file. Only one (-file07) which have "ASCII text" type is readable.

# Level 5 -> Level 6
Solution 1 (works): find inhere -size 1033c
Solution 2 (appropriate - matching requirements): find inhere -size 1033c \! -executable -exec file {} + | grep "ASCII text"
Explanation: Using the first solution is sufficient, as there are no other files of this size in this directory. However, assuming there are more, the second solution should be used, which searches for these files according to the specified requirements. The find command does not have an option to check whether a file is human-readable (not to be confused with the -readable option, which indicates files we are authorized to read). Therefore, we must also invoke the file command using -exec. The -exec command passes the output of the preceding command to its argument. The file path is enclosed in curly braces ("{ }"), and the "+" indicates that find must first find all files before passing them to the file command. The most common alternative to "+" is "/." In this configuration, find will call file for each file found.
