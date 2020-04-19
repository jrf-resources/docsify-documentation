# How to remove last character
Remove the last character from a variable via the following:
```bash
VAR="Variable"
VARNEW=${VAR%?};
echo $VARNEW # --> Variabl
```