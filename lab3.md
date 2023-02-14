# Lab Report 3 - Researching Commands

Let's look at some command-line options for the `find` command.

## -empty

Attaching `-empty` will specify `find` to only return empty files or folders (found [here](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/)). Here is an example of using this command in `./written_2`:

    $ docsearch % find ./written_2/non-fiction -empty
    $ docsearch %

As you can see, there are no empty files or folders in the sub-directory `non-fiction`. Let's see what happens with the other sub-directory in `./written_2`:

    $ docsearch % find ./written_2/travel_guides -empty
    $ docsearch %

Once again, nothing is returned so `travel_guides` also contains no empty files or directories. The `-empty` option could be helpful for tracking down empty files in a large directory which can simply be discarded (decluttering).

## -type

You can use `-type t` to narrow the search to only be items of type `t`, such as `f` for file or `d` for directory (I discoverd this option by asking ChatGPT). For example, we have:

    $ docsearch % find ./written_2/non-fiction -type d
    ./written_2/non-fiction
    ./written_2/non-fiction/OUP
    ./written_2/non-fiction/OUP/Berk
    ./written_2/non-fiction/OUP/Abernathy
    ./written_2/non-fiction/OUP/Rybczynski
    ./written_2/non-fiction/OUP/Kauffman
    ./written_2/non-fiction/OUP/Fletcher
    ./written_2/non-fiction/OUP/Castro
    $ docsearch %

Now we know all of the directories contained in `written_2/non-fiction`. Another example:
-type ex 2

    $ docsearch % find ./written_2/non-fiction/OUP/Berk -type f 
    ./written_2/non-fiction/OUP/Berk/ch2.txt
    ./written_2/non-fiction/OUP/Berk/ch1.txt
    ./written_2/non-fiction/OUP/Berk/CH4.txt
    ./written_2/non-fiction/OUP/Berk/ch7.txt
    $ docsearch %

Now we know all of the text files that are contained in `written_2/non-fiction/OUP/Berk`. If one wanted to count the number of files in a directory, it would make sense to use `-type f` so that folder are ignored in the search. A use of `-type d` might be to learn the folder hierarchy of a directory quickly.

## -size

The `-size N` option can be used to find files or directories of size `N` blocks, or `Nc` to make characters the unit of size. `+` indicates we want files greater in size, and `-` indicates less than (found [here](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/)). Let's see an example:

    $ docsearch % find ./written_2/non-fiction -type f -size +100000c
    ./written_2/non-fiction/OUP/Berk/ch2.txt
    ./written_2/non-fiction/OUP/Berk/CH4.txt
    $ docsearch % 

This command searched for files (using `-type f`) with 100,000 or more characters. As we can see, only two text files in `written_2/non-fiction` satisfy this. Here's another example:

    $ docsearch % find ./written_2/non-fiction -type f -size -10000c 
    ./written_2/non-fiction/OUP/Castro/chQ.txt
    ./written_2/non-fiction/OUP/Castro/chW.txt
    ./written_2/non-fiction/OUP/Castro/chZ.txt
    ./written_2/non-fiction/OUP/Castro/chN.txt
    ./written_2/non-fiction/OUP/Castro/chY.txt
    ./written_2/non-fiction/OUP/Castro/chO.txt
    $ docsearch %

This command is very similar, except it searched for files smaller than 10,000 characters. It could helpful to figure out which files surpass a certain size threshold so that it is clear which files are particularly large or small, which could be helpful for data management.

## -newer

The `-newer item` option returns all items that were created after `item` (found [here](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/)). Here's an example:

    $ docsearch % find ./written_2/non-fiction -type f -newer ./written_2/non-fiction/OUP/Rybczynski/ch2.txt
    ./written_2/non-fiction/OUP/Rybczynski/ch3.txt
    $ docsearch %

This may seem contrived, but now we know the only file in `/written_2/non-fiction` that was created after `ch2.txt` is `ch3.txt`. So is `ch3.txt` the oldest file in our directory? Let's see:

    $ docsearch % find ./written_2/non-fiction -type f -newer ./written_2/non-fiction/OUP/Rybczynski/ch3.txt
    $ docsearch %

As you can see, running `-newer` on `ch3.txt` returns nothing, so it is indeed the newest file in `/written_2/non-fiction`.