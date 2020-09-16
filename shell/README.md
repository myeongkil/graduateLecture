# Shell
* UNIX command interpreter
* just one of the user programs

------------------
## bash shell features
* Read and interpret
* customize
* abbreviate long names
* save old commands(history)
* job control (foreground / background)
* high level programming(script)

------------------
## bash setup files

### .bash_profile
* when user logs in
* settings necessary

### .bash_logout
* when user logs out

### .bashrc
* execute by each shell
* every time it executes a script
------------------
## Command Substitution

### Using Backquote
* ` : backquote
```
$ d=`date` && echo $d
```

### Using $()
```
$ ls $(pwd)
```
------------------
## Command Group

### (command1;command2;command3)
```
$ pwd
> ~/src/github.com/myeongkil/shell
$ (mkdir down; cd down; echo hello)

$ pwd
> ~/src/github.com/myeongkil/shell

$ ls
> README.md down

$ rm -rf down
```

> pwd 시 왜 원래 디렉토리가 유지되는가? \
> command가 실행될 때, child-shell(sub-shell)을 통해 실행을 마치고, \
> 이후 parent-shell로 돌아오기 때문
------------------
## I/O redirection

`>`, `>>` : this command can destroy file
```
# enable protect option, for prevent overwrite
set -o noclobber

# disable protect option
set +o noclobber
```
------------------
## Job control

`&` : background job

```
$ ls -l > dir.list &
```
------------------
## Conditional command

`&&` : if succeed  \
`||` : if fail

```
# if grep succeeds, then execute echo
$ grep kmk shell_sample.txt && echo success
> kmk     3.75    10  KOREA
> success

# if grep fails, then execute echo
$ grep kmk shell_sample.txt || echo fail
> kmk     3.75    10  KOREA
```
------------------

# SHELL?

## 1. language(very high level script program)
## 2. interpreter(read & execute each line)
## 3. uses other components
## 4. glues them together
## 5. Convenient language
* weekly defined
* slow but powerful & easy (interpreter)
* quick prototyping
* system programming(high level)