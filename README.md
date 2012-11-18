code-snips
==========
Little bits of code I need but don't recall

### Count occurence of every character in a file
Source:
http://www.unix.com/shell-programming-scripting/47239-count-occurances-character-file.html

```bash
awk '{ for ( i=1; i<=length; i++ ) arr[substr($0, i, 1)]++ }END{ for ( i in arr ) { print i, arr[i] } }' filename.txt
```

### Save file in vim as root
```vim
:w !sudo tee %
```

### Format align columns of tab delim output:
```bash
column -t -s"   " file
```

### BASH Input Handling. Default file, passed in file, or stdin
Sources: 
http://stackoverflow.com/questions/6980090/bash-read-from-file-or-stdin
http://stackoverflow.com/questions/2456750/detect-presence-of-stdin-contents-in-bourne-shell
```bash
DEF_INPUT=file.txt
if [ -t 0 ]; then
  if [[ -z $1 ]]; then
    INPUT="$DEF_INPUT"
  else
    INPUT="$1"
  fi
else
  INPUT=/dev/stdin
fi

while read line;
  do echo $line
done < $INPUT
```

### Drop all tables in Oracle 
Source: 
http://stackoverflow.com/questions/842530/plsql-drop-all-database-objects-of-a-user
```sql
declare
  cursor ix is
    select *
      from user_objects
     where object_type in ('TABLE', 'VIEW', 'FUNCTION', 'SEQUENCE');
begin
 for x in ix loop
   execute immediate('drop '||x.object_type||' '||x.object_name);
 end loop;
end;
```
