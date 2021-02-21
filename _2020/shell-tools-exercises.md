1. `ls -AtlhG`. Options:
- `A`: list all file include hidden files and directories (dotfile, dot directory) 
- `t`: sort by time last access
- `l`: list long format
- `h`: show size in human readable
- `G`: enable colorize output, to setting color `export LSCOLORS=<color in order>`
2. macro.sh
```shell
  macro () {
    current_dir=$(pwd)
    export MACRO="$current_dir"
  }

  polo () {
    if ($MACRO) {
      cd $MACRO
    }
  }
```
and then run `source macro.sh`
3. 
```shell
  #!/bin/bash

  count=0
  while [[ true ]]
  do
    ((count++))
    ./fail-script >> log
    if [[ $? -eq 1 ]]; then
      echo "failed with $count tries!"
      echo $(tail -1 log)
      break
    fi
  done
```
4. `find  . -name "*.html" -print0 | xargs -0 tar -cvf archive.tar`
- use `find` to find files in current directory with pattern `*.html`
- option `print0` to make output separate with **NUL** (\`\`0'')
- `xargs` to make standard output as arguments of next command, here is `tar`
- option `0` make argument split with **NUL** (\`\`\0'') instead of spaces or newlines.
- `tar` to create archive file with option `-c`
- `-v` to verbose, and `-f <file>` to specified output file name
5. `find . -type f -print0 | xargs -0 -n1 stat -f '%Sm %N' -t '%Y-%m-%d %H:%M:%S' | sort -nr | head -n 1`
- `find` to find all file in current directory
- `stat` to show metadata of file in specific format with time in first
- `sort` to sort by time (option `-n`: numeric, `-r`: reverse)
- `head` to get first line of output
