# Data wrangling exercises 

1. Find most common 2 letter
```bash
    cat /usr/share/dict/words | tr "[:upper:]" "[:lower:]" | awk '$0 ~ /^(.*a.*){3}$/ { print $0 }' | awk '$0 ~ /^(.+[^s])$/ { print $0 }' | sed -E 's/^.*(.{2}$)/\1/g' | uniq -c | sort -nk1,1 | tail -n3 | awk '{ print $2 }'
```
