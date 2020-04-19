# How to kill all processes with certain name 
```bash
ps aux | grep "processname" | awk '{ print $2 }' | xargs kill
```