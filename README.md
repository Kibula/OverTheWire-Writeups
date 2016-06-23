# OverTheWire Bandit

Level 0 -> 1

> Find the password to level 1 stored in a text file. A simple cat command.
```sh
cat readme
```

Level 1 -> 2

>This time the text file's name is - therefore can't open with a cat command. 
>Had to give the absolute path to open the file.
```sh
cat /home/bandit1/-
```

Level 2 -> 3

>There's a file with spaces in the file name. Would give an error when tried to open the usual way. Need to add escape character to define spaces in the name
```sh
cat spaces\ in\ the\ file\ name
```

Level 3 -> 4

>Next password is hidden inside a folder. Had to find it and open

```sh
cd inhere
ls -a
cat .hiden
```

Level 4 -> 5

>Password hidden in one file that's human readable with another 8 files non-human readable. 

Level 5 -> 6

>Password hidden inside a folder with compressed files and other files. Had to search for the given parameters

```sh
find -size 1033c -not -executable | xargs file
```

Level 6 -> 7

>Password hidden in an unknown location on the server. Had to search every directory for the pecified attributes.

```ssh
 find / -user bandit7 -group bandit6 -size 33c
cat /var/lib/dpkg/info/bandit7.password
```

Level 7 -> 8

>Password hidden in a text file with large number of lines. Clue says it's the one next to the word "millionth". Had to search lines containing the word "millionth"\

```sh
grep "millionth" data.txt
```
this code shoewd the lines matching along wth the password


Level 8 -> 9

>Password hidden in a file with another lot of passwords. Clue says it occurs only once. Had to sort and find the ones that occurs only once.

```sh
sort data.txt | uniq -u
```

Level 9 -> 10 

>Password hidden in a non-ascii file with some strings in it. had to find strings and strings containing == characters

```sh
string data.txt | grep "=="
```

LEVEL 10 -> 11
>Password hidden in a base64 encoded file. Simply decoding the file would give the password

```sh
cat data.txt | base64 --decode
```

Level 11 -> 12

>Password is encrypted with ROT13

```sh
cat data.txt | tr 'a-z' 'n-za-m' | tr 'A-Z' 'N-ZA-M'
```

Level 12 -> 13

>Password hiden in a hex dump that's been compressed multiple times. Had to convert hexdump to bin and then decompress it pultiple times

```sh
xxd -r data.txt | data.bin
zcat data.bin | bzcat | zcat | tar xO | tar xO | bzcat | tar xO | zcat | cat
```

Level 13 -> 14
>SSH key is stored in a file and had to submit it to the login to get into next level
```sh
ssh bandit14@localhost -i ~/sshkey.private
```

Level 14 -> 15

>Password id stored in the previously specified folder and have to submit it to port 30000

```ssh
telnet localhost 30000
```

this gave the password for the next level

Level 15 -> 16





