2. Use git command
- Explore version history by graph: `git log --graph --decorate`
- Last person modified `README.md`: `git log -- README.md`
- Show the commit message associated with the last modification to the collections: line of \_config.yml:
```git
git blame _config.yml
git show a88b4eac
```
3. Remove mistake commit:
- Force Git to process, but not check out, the entire history of every branch and tag
- Remove the specified file, as well as any empty commits generated as a result
- Overwrite your existing tags
```git
  git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA" \
  --prune-empty --tag-name-filter cat -- --all
```

5. 
``` 
[alias]
   graph = log --all --graph --decorate --oneline
```
