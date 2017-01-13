#Theme watch returns error - too many open files
When you run theme watch in your console and returns error too many open files you should run:

`ulimit -u` = returns the set up allowed number of files

`sudo ulimit -n 4096` - increases the max number of files to 4096