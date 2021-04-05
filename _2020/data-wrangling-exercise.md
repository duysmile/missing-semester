# Data wrangling exercises 

1. Find most common 2 letter
```bash
    cat /usr/share/dict/words \
    | tr "[:upper:]" "[:lower:]" \ 
    | awk '$0 ~ /^(.*a.*){3}$/ { print $0 }' \
    | awk '$0 ~ /^(.+[^s])$/ { print $0 }' \
    | sed -E 's/^.*(.{2}$)/\1/g' \
    | uniq -c | sort -nk1,1 | tail -n3 | awk '{ print $2 }'
```
- First read file `words` by `cat` command
- Second, lower case all text by `tr`
- Next, use regex to filter all word has at least 3 `a` characters by `awk`
- Then, continue using regex to filter all words have `s` ending by `awk`
- Next, use `sed` to replace all words by their last two characters
- Then, combine `uniq -c` to get list unique word with number of appearance and `sort -nk1,1` to order them by frequency of appearance.
- Last, just get 3 most common last two letters by `tail`.
