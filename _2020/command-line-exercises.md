# Command line exercises

### Job control
1. Use pgrep and pkil
```bash
sleep 10000
bg
jobs
pgrep sleep
pkill sleep
jobs
```
2. Use wait to start process until another completes
```bash
sleep 60 &
pgrep -af "sleep 60" | wait && ls
```
pidwait
```bash
pidwait() {
    while kill -0 $1 2>/dev/null
    do
        sleep 1
    done
}
```
Run command
```bash
source ./pidwait.sh
pidwait <PID> && ls
```

3. Remote machines
- Use `mutlipass` to create Virtual Machines
```bash
brew install --cask multipass
multipass launch --network en0 --network name=bridge0,mode=manual --name ubuntu-20
```
