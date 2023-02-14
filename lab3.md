# Researching Commands  

<br>
For this lab, we will be working with the `find` command, discovering some interesting functionality along the way. All information has been gathered from this website: https://www.booleanworld.com/guide-linux-find-command/.
<br>

## `-type`

<br>
<br>

The `-type` flag specifies the type of item the command is searching for - either a file or a directory. `-type f` searches only for files, while `type d` searches only for directories. 

<br>
<br>

Example of `-type f`:

```
$ find written_2 -type f
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Abernathy/ch14.txt
written_2/non-fiction/OUP/Abernathy/ch15.txt
written_2/non-fiction/OUP/Abernathy/ch2.txt
written_2/non-fiction/OUP/Abernathy/ch3.txt
...
written_2/travel_guides/berlitz2/Budapest-WhereoGo.txt
written_2/travel_guides/berlitz2/California-History.txt
written_2/travel_guides/berlitz2/California-WhatToDo.txt
```

<br>
This printed out all files in the written_2 directory and all subdirectories.
<br>
<br>

Example of `-type d`:

```
$ find written_2 -type d
written_2
written_2/non-fiction
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Abernathy
written_2/non-fiction/OUP/Berk
written_2/non-fiction/OUP/Castro
written_2/non-fiction/OUP/Fletcher
written_2/non-fiction/OUP/Kauffman
written_2/non-fiction/OUP/Rybczynski
written_2/travel_guides
written_2/travel_guides/berlitz1
written_2/travel_guides/berlitz2
```

<br>
This printed out all directories within written_2. The `find -type` command, as we can see, may be quite useful for instances where only files or directories work for a particular application, and need to be separated from the mix.
<br>
<br>

## `-empty`

<br>

The `-empty` flag causes the find command to search for only empty files of directories. This can be combined with the `type` flag mentioned earlier. To demonstrate this, I added two new items to the `written_2` directory: an empty file named `empty.txt` and an empty directory named `emptyDir`.

<br>
<br>
File:
<br>

```
$ find written_2 -type f -empty
written_2/empty.txt
```

<br>
Directory:
<br>

```
$ find written_2 -type d -empty
written_2/emptyDir
```

<br>

As can be seen, the two commands did what was expected: the first one found the only empty file in `written_2`, while the second command found the only empty directory. This command is useful for times when empty files or directories need to be isolated or potentially removed.

<br>
<br>

## `-mtime`

<br>
<br>

The `-mtime` flag filters results by how long ago a file was last modified. The default measurement is in days (i.e `-mtime 1` would look for files that were modified one day ago). A `+` or `-` can also be added before the number to include files modified before or after the given day. Here are some examples:

<br>
<br>

Searching for files modified today:

<br>

```
$ find written_2 -type f -mtime 0
written_2/empty.txt
```

<br>
<br>

Searching for files modified yesterday or before:
<br>

```
$ find written_2 -type f -mtime +1
written_2/non-fiction/OUP/Abernathy/ch1.txt
written_2/non-fiction/OUP/Abernathy/ch14.txt
written_2/non-fiction/OUP/Abernathy/ch15.txt
...
written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt
written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt
```

<br>

As we can see, the first command printed only `empty.txt`, the empty text file I added to demonstrate the previous command. The second command prints out every other file in the directory, as they were all created well before yesterday and haven't been modified since. This command can be useful in many capacities, an example being in any sort of 'sort by recent' tool. 

<br>
<br>

## `-size`

<br>

The `-size` flag allows a user to search files (not directories) with a specific size. This command can also be modified with + or -, as in the previous example. In this example, we will be searching for files that are 16 kb and for files that are smaller than 16 kb. 

<br>
<br>

Searching for files that are 16 kb:

<br>

```
$ find written_2 -type f -size 16k
written_2/travel_guides/berlitz1/HistoryDublin.txt
written_2/travel_guides/berlitz2/Algarve-History.txt
written_2/travel_guides/berlitz2/Algarve-WhatToDo.txt
written_2/travel_guides/berlitz2/Amsterdam-History.txt
written_2/travel_guides/berlitz2/Amsterdam-WhatToDo.txt
written_2/travel_guides/berlitz2/California-WhatToDo.txt
written_2/travel_guides/berlitz2/CanaryIslands-WhatToDo.txt
written_2/travel_guides/berlitz2/Cancun-History.txt
written_2/travel_guides/berlitz2/Costa-History.txt
written_2/travel_guides/berlitz2/Crete-History.txt
```

<br>
<br>

Searching for files that are at most 16 kb:

<br>

```
$ find written_2 -size -16k
written_2/empty.txt
written_2/non-fiction/OUP/Castro/chN.txt
written_2/non-fiction/OUP/Castro/chO.txt
written_2/non-fiction/OUP/Castro/chQ.txt
...
written_2/travel_guides/berlitz2/Portugal-History.txt
written_2/travel_guides/berlitz2/PuertoRico-History.txt
written_2/travel_guides/berlitz2/Vallarta-History.txt
```

<br>
<br>

This flag is useful to search for files of a particular size, or if there is a limit or minimum on file size that must be considered for some application.
