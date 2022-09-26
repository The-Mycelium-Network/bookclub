# Tools of the terminal trade

## The `|` (pipe) chracter

> The pipe is a magic and integral part of the command line. It’s super powerful and extremely useful. What it does is take the output from the first command (on the left side) and “pipe” it to the second command (on the right side).

To read the docs for most commands you can type `man util-name`, for example `man grep`.

## grep

- [grep manual page online](https://manpages.org/grep/1)

We can highly recommended you look at [`ripgrep`](https://github.com/BurntSushi/ripgrep) as an alternative to `grep`.

> ripgrep is a line-oriented search tool that recursively searches the current directory for a regex pattern. By default, ripgrep will respect gitignore rules and automatically skip hidden files/directories and binary files. ripgrep has first class support on Windows, macOS and Linux, with binary downloads available for every release. ripgrep is similar to other popular search tools like The Silver Searcher, ack and grep.

### ripgrep example

At the end of the chapter there is this command Remy uses:

```bash
tail -1000 access.log  | cut -d' ' -f1 | sort | uniq -c | sort -n | tail -5
```

Using ripgrep you can get the same result like this:

```bash
rg "(\d+(\.|(?: )){1}){4}" -o access.log -N | uniq -c | sort | tail -5
```

- `"(\d+(\.|(?: )){1}){4}"` is a regular expression that matches the IP addresses
- `-o` will only print the matched part of the string
- `-N` tells ripgrep to not output the line number

`rg "(\d+(\.|(?: )){1}){4}" -o access.log -N` will output something like:

```bash
192.241.205.217
20.243.176.69
20.243.176.69
20.243.176.69
51.79.29.48
81.0.4044.129
51.79.29.48
81.0.4044.129
5.181.80.56
154.6.22.115
60.0.3112.107
154.6.22.115
60.0.3112.107
174.138.61.44
174.138.61.44
174.138.61.44
51.79.29.48
81.0.4044.129
51.79.29.48
81.0.4044.129
181.214.218.69
41.0.2224.3
```

## less

### less cheatsheet

- move up and down using the up and down arrow keys
- Page forward by pressing the space key
- Page backward by pressing B
- Start a search by pressing /
- Move to the next match with N
- To quit less, press Q

- [less manual page online](https://manpages.org/less/l)

## tail

- [tail manual page online](https://manpages.org/tail)

### Related learning

- [/Reg(exp){2}lained/: Demystifying Regular Expressions](https://www.youtube.com/watch?v=EkluES9Rvak)
- [Interactive RegExp Tools](https://developer-toolchest.com/?q=regex)
- [Modern Unix](https://github.com/ibraheemdev/modern-unix)
