
# Tools
### Filtering Tools
Show first x amount of lines of file:
```bash
head -20 log.txt # shows first 20 lines
```
Show last x amount of lines of file:
```bash
tail -30 log.txt # shows last 30 lines
```
Sort a file alphabetically:
```bash
sort list.txt
```
Number each line of a file:
```bash
nl list.txt
```
Display word count, character count, and line count of a file:
```bash
wc -c -w -l list.txt
```
Split a file into columns and return the selected column:
```bash
cut -f 1 -d ' ' table.txt
```
Search for a value in a file and replace it with a new value:
```bash
sed s/value1/value2/g list.txt
```
Print only second column of top:
```bash
top | awk '{print $2}'
```
Print lines where column 3 is greater than 10, and reformat columns:
```bash
awk '$3 > 10 {print $1 " - " $2 " : " $3}' file.txt
```
Remove duplicate adjacent lines from a file:
```bash
uniq list.tx
```
### Search Tools
Find the location of a file:
```bash
locate filename
```
Search the root directory for keyword:
```bash
find / -iname keyword
```
Search home directory for files over 200MB and then list files:
```bash
find /home -size +200M -exec ls -sh {} \\;
```