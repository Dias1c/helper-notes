# Tricks of bash commands

## Using `>`
`>` - writes output data to file
> If file exists, he will rewrite file

Usage:
```bash
$ {command} > {filename}
```

Example:
```bash
# Writes "Hello" to file.txt
$ echo "Hello" > file.txt
```

## Using `|`
`|` - sends output to next function

Usage:
```bash
$ {command} | {command}
```

Example:
```bash
# Sends output "Hello Lucy" to func grep
$ echo "Hello Lucy" | grep -o "l"
l
l
```

## Using `&&`
`&&` - executes commands in turn

Usage:
```bash
$ {command} && {command}
```

Example:
```bash
$ echo "Executed first" && echo "Executed second"
Executed first
Executed second
```

## Using `` && `$()`
`` or `$()` - returns value of command

Usage:
```bash
$ `command`
# or
$ $(command)
# They are both the same
```

Example:
For example we want get count of letter "l" in file
```bash
$ cat file.txt
Hello World
# Writes result of commands in `` to $CntL and $() to $CntChars
$ CntL=`grep -o l file.txt | wc -l` && CntChars=$(cat file.txt | wc -c)
# Shows result by echo using $CntL and $CntChars
$ echo "File file.txt has $CntChars chars and $CntL 'l' letter"
File file.txt has 12 chars and 3 'l' letter
```
