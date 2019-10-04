---
layout: post
title: "A very short list of UNIX commands to get started"
author: "Martym"
categories: computer
tags: []
---

# A very short list of UNIX commands to get started

## Commands

- `man` -- manual

At the bottom, there is usually a `SEE ALSO` section, where you can
find other commands.

- `ps` -- process status

I just memorise `ps aux` that seems to give what I want

- `find` -- walk a file hierarchy

`find . -type f` -- Find files
`find . -type d` -- Find directories

`find . -type f -name *go` -- Find go files

- `grep` and friends -- file pattern searcher

I only use `grep`. Here are the common options:

`grep -c` -- the number of lines found
`grep -v` -- Selected lines are those not matching any of the specified patterns.
`grep -i` -- Perform case insensitive matching.
`grep -H` -- Print filename headers with output lines.

- `xargs` -- construct argument list(s) and execute utility

`find . -type f -name *rb | xargs -n 1 grep ^require` -- For each line (`-n 1`)
of the output of `find`, run `grep require <each line from
find>`. Basically, find all the `require` in your ruby source files.

- `sed` -- stream editor

`sed -e 's/test_file/file/g' source.rb` -- Replace every `test_file`
with `file` in `source.rb`. Without `g`, it will only replace the first
occurrence in each line.
g
- An example - Can you explain what the line below does?

``` shell

find . -type f | xargs -n 1 grep 'require ' | uniq | sort | sed -e's/require //' -e 's/"//g' -e 's/^/gem /'`

```
