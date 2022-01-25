# Tricks of bash commands

## Using `|`
`|` - chains commands together. It takes the output from one command and feeds it to the next as input.

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

## Using `` && `()`
`` or `()` - returns value of command

Usage:
```bash
$ `command`
# or
$ (command)
# Important for brackets. Use "$" if you sends value of commands with using pipe "|" to variable
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

## Using `<`
Many Linux commands accept a file as a parameter and take their data from that file. Most of these commands can also take input from a stream. To create a stream, you use the left-angle bracket `<`, as shown in the following example, to redirect a file into a command:

Usage:
```bash
$ {command} < {filename}
# Or
$ {command} <({command with output})
```

Example:
```bash
# command "sort" takes only filename but also he can input stream
$ sort < numbers.txt
1
5
9
```

```bash 
$ sort <(echo -e "9\n3\n5" && echo -e "1\n4\nD")
1
3
4
5
9
D
```
