code-snips
==========

Little bits of code I need but don't recall

# Count occurence of every character in a file
# Credit: matrixmadhan http://www.unix.com/shell-programming-scripting/47239-count-occurances-character-file.html

awk '{ for ( i=1; i<=length; i++ ) arr[substr($0, i, 1)]++ }END{ for ( i in arr ) { print i, arr[i] } }' filename.txt
