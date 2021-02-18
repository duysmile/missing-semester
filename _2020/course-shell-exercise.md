`ls -l`: listing long format
- `permission drwxr-xr--`: `d` is directory, 3 group correspond to owner, group owner, all user in system.
5. `echo '#!/bin/sh' | tee semester | echo 'curl --head --silent https://missing.csail.mit.edu' | tee -a semester`
  - use single-quote (') to treat special character in `shell`
  - `tee` to open a stream to copies standard input to standard output
  - use option `-a` to append to output file rather than overwritting.
7. use `sh` can run `semester` file because it can excecute command contained in that file so you just need read permission, and that file cannot be executed directly becuz it don't have permission to excecute `x`.
  - Solution: use `chmod`
  - Reference: https://unix.stackexchange.com/questions/136547/what-is-the-difference-between-running-bash-script-sh-and-script-sh?rq=1
9. `chmod 733 semester`
10. `./semester | grep "last-modified:" | cut -c16- > last-modified.txt`
  - `grep` to get line has string `last-modified:`
  - `cut` command to get a substring, use option `-c<start-position>-<end-position>` to get substring from start to end (if end is omitted that means to end of string)
11. MacOS
  - Show battery: `system_profiler SPPowerDataType | grep "State of Charge" | awk '{print $5}'`
  - Show CPU temperature: `sudo powermetrics --samplers smc |grep -i "CPU die temperature"`
  - `awk` command to get string split by space(' ') in order of input string

`Shebang` is character sequence consisting of the characters number sign and exclamation mark (**#!**).
When a text file with a shebang is used as if it is an executable in a Unix-like operating system, the program loader mechanism parses the rest of the file's initial line as an interpreter directive. The loader executes the specified interpreter program, passing to it as an argument the path that was initially used when attempting to run the script, so that the program may use the file as input data. For example, `#!/bin/sh`.
