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
4. 
