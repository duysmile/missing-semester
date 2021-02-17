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
