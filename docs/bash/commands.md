# Command Management
### Man Pages
Look up the man page for a command:
```bash
man command_name
```
Search all man pages for keyword:
```bash
man -k keyword
```
Display matching man pages:
```bash
whatis command_name
```
Search man page descriptions for keyword:
```bash
apropos keyword
```
### Pipeline Tools
Pipe one command to another command:
```bash
ls -al | head -3 # show only first three directorys from ls command
```
Write output of command to file:
```bash
ps aux > processes.txt
```
Append output to file:
```bash
ps aux >> processes.txt
```
Feed file into command:
```bash
command < folders.txt
```
Output error stream to file:
```bash
nginx -t 2> errors.log
```
### Miscellaneous Commands
Locate binary and manual of a command:
```bash
whereis command_name
```
Return paths of commands:
```bash
which command_name
```
The following command lets you bypass any shell aliases.
```bash
command command_to_execute
```
How to get the exit status of piped command:
```bash
command1 | command2
echo "${PIPESTATUS[@]}"
```
Display all builtin bash commands:
```bash
help
```
Find out if a command os internal or external:
```bash
type -a command_name
```