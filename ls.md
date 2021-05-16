# LS

## Sort by name

The ls command displays the contents of a directory by the file/folder names by default. You can view a vertical list of the directory contents, sorted name wise, explicitly through the following command:

~~~~
$ ls -1
~~~~
## Sort by size

In order to view the contents of a directory, sorted on the basis of size, use the following command:

~~~~
$ ls -S
~~~~
## Sort by modification date

In order to view the contents of a directory, sorted on the basis of the date of modification, use the following command:

~~~~
$ ls -t
~~~~
## Sort by last access time

In order to view the contents of a directory, sorted on the basis of the last time of access, use the following command:

~~~~
$ ls -ut
~~~~
Sort by date of creation

In order to view the contents of a directory, sorted on the basis of the date of creation, use the following command:

~~~~
$ ls -Ut
~~~~
## Sort by extension

In order to view the contents of a directory, sorted on the basis of file extension, use the following command:

~~~~
$ ls -X
~~~~
## How to reverse sort any order

In order to reverse the sort order you specified through a flag in the sort command, simply add the ‘r’ flag with the already specified flag.

For example, the following command will print the output of the ls command in reserve order of size:

~~~~
$ ls -Sr
~~~~
By following the ways defined in this article, you can now sort the contents of a directory based on your preferences, both in the UI and the command line.
