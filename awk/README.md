# AWK Language
Shell 에서 사용하는 유틸리티 툴 / 텍스트를 다루는데 사용
일정한 패턴을 가진 로그 데이터 처리에 유용함

```
sample.txt
lol     4.00     0  USA
kmk     3.75    10  KOREA
pnu     5.50    20  PUSAN
kim     1.50    30  0
```

## 1. simple test
> awk `pattern` `data`

```
$ awk '$3>0 {printf("%s\n", $1)}' sample.txt
> kmk
> pnu
> kim
```

## 2. BEGIN / END

```
$ awk 'BEGIN{print "Header line here"} $3>15 {emp=emp+1} END{print emp}' sample.txt
> Header line here
> 2
```

## 3. Regular expreesions

```
## 4th field contains 'KOREA'
$ awk '$4 ~/KOREA/ {printf("%s\n", $1)}' sample.txt
> kmk

## line doesn't contains 'KOREA'
$ awk '$0 !~/KOREA/ {printf("%s\n", $1)}' sample.txt
> lol
> pnu
> kim

## 2nd field not a string of digits
$ awk '$2 !~/^[0-9]+$/ {printf("%s\n", $1)}' sample.txt
> lol
> kmk
> pnu
> kim
```

## 4. arithmetic functions

* just google
* `atan2(y,x)`, `log(x)`, `rand()` ...

## 5. Statement

* just google
* `if`, `if else`, `while`, `for`, `do while`, `break`, `continue`

## 6. Range Patterns

> awk pattern1 pattern2 {Action}

------------------------

Awk is
* a UNIX command
* Interpreter(line by line, pattern match & take action)
* Text processing tool
* Filter