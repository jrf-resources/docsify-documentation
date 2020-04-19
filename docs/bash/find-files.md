# How to Find Files
### locate
```bash
# Normal syntax
locate filename
# Ignore case
locate -i filename
# Only find and limit search to one file at a time
locate -n 1 filename
# Find exact filename match
locate -b '\\FILENAME'
# Find information about current databased created by the updatedb command
locate -S
```

### find
```bash
# Basic syntax
find /path/to/dir -name "filename"
# Ignore case
find /path/to/dir -iname "filename"
# Find directories in root
find / -type d -name foldername
# Find files in root
find / -type f -name file.ext
# Find all files with same extension in root
find / -type f -name *.ext
# Find all files with 755 permissions in cwd
find . -type f -perm 0755 -print
# Find all files without 755 permissions in root
find / -type f ! -perm 755
# Find all executable files
find / -perm /a=x
# Find Files with 777 Permissions and Chmod to 644
find / -type f -perm 0777 -print -exec chmod 644 {} \\;
# Find Directories with 777 Permissions and Chmod to 755
find / -type d -perm 777 -print -exec chmod 755 {} \\;
# Find and remove a single file
find / -type f -name "file.txt" -exec rm -f {} \\;
# Find and remove multiple files
find / -type f -name "*.txt" -exec rm -f {} \\;
# Find all empty files
find /tmp -type f -empty
# Find all empty directories
find /tmp -type d -empty
# Find all hidden files
find /tmp -type f -name ".*"
# Find all files owned by user
find /home -user jac
# Find all files based on group
find /home -group root
# Find all files which are modified 50 days back
find / -mtime 50
# Find all files which are accessed 50 days back
find / -atime 50
# Find files modified between 50 and 100 days ago
find / -mtime +50 –mtime -100
# Find files modified in the last hour
find / -cmin -60
# Find files that are 50MB
find / -size 50M
# Find files that are between 50MB and 100MB
find / -size +50M -size -100M
# Find all 100MB files and delete them
find / -size +100M -exec rm -rf {} \\;
```
