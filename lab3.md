# Researching Commands  

<br>
For this lab, we will be working with the `find` command, discovering some interesting functionality along the way. All information has been gathered from this website: https://www.booleanworld.com/guide-linux-find-command/.
<br>

## `type`

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
This printed out all directories within written_2. 
