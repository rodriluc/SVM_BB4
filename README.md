# SU-project

PS1="$"
$man ls -> list all and search for something with /'text'
back N - forward n -> got through search
$cd .. -> move up one directory
$cd -> return you to your home directory
~data = /Users/nelle/data
$nano draft.txt -> text editor
  Ctrl-o to write data to disk
  Control=Ctrl=^     all mean the same thing
  Ctrl-X toquit editor and return to shell
$touch my_file.txt  -> generates new file called my_file.txt in home directory
$rm draft.txt  -> removes files FOREVER not directories
  rm -r thesis (to get rid of directory have to remove file in it as well)
$pwd -> shows you where you are
$cd something -> brings you to something directory
  $ cd Desktop/data-shell/data
    tell it to follow this string
$ls -> shows you everything
$ mv thesis/draft.txt thesis/quotes.txt
  to change file name
$ ls -F Desktop
  The argument Desktop tells ls that we want a listing of something other than our current working directory
  Your output should be a list of all the files and sub-directories on your Desktop, including the data-shell directory 
$ mv ../analyzed/sucrose.dat ../analyzed/maltose.dat .
  Recall that .. refers to the parent directory (i.e. one above the current directory) and that . refers to the current directory
$ cp quotes.txt thesis/quotations.txt
  cp commands works very much like mv, except it copies a file instead of moving it
$ mkdir backup
$ cp amino-acids.txt animals.txt backup/
  If given more than one file name followed by a directory name (i.e. the destination directory must be the last argument), 
  cp copies the files to the named directory
* wild card to match all files and subdirectories
  rm 2016-05-20-data/raw/*
    here it will remove all files in raw directory but leave the raw directory there
  ls -l *.txt
    shows a list of all txt
    
Pipes and Filters

wc *.pdb
  wc is the “word count” command: it counts the number of lines, words, and characters in files
?  -> wildcard but it only matches a single character 
  p?.pdb would match pi.pdb or p5.pdb (if we had these two files in the molecules directory), but not propane.pdb
  ls *t??ne.pdb
    fixes the problems of option 2 by matching two characters between t and ne
$ wc -l *.pdb  -> number of lines
  -w words
  -c characters
$ wc -l *.pdb > lengths.txt
  The greater than symbol, >, tells the shell to redirect the command’s output to a file instead of printing it to the screen
$ echo hello >> testfile02.txt
  appends data to that testfile02.txt
$ head -3 animals.txt > animalsUpd.txt
$ tail -2 animals.txt >> animalsUpd.txt
  The first three lines and the last two lines of animals.txt
$ cat lengths.txt
  send the content of lengths.txt to the screen using cat lengths.txt. cat stands for “concatenate”: 
  it prints the contents of files one after another. 
  There’s only one file in this case, so cat just shows us what it contains
Better to use less than cat
$ less lengths.txt
  displays a screenful of the file, and then stops. You can go forward one screenful by pressing the spacebar, 
  or back one by pressing b. Press q to quit
$ sort -n lengths.txt
  use the -n flag to specify that the sort is numerical instead of alphabetical
$ head -n 20 sorted-lengths.txt
  gives the first 20 lines of that file
$ sort -n lengths.txt | head -n 1
  vertical bar, |, between the two commands is called a pipe. 
  It tells the shell that we want to use the output of the command on the left as the input to the command on the right
$ wc -l *.pdb | sort -n | head -n 1
  pipe character | is used to feed the standard output from one process to the standard input of another. 
  > is used to redirect standard output to a file
$ wc -l < notes.txt
  use < to redirect its input, i.e., to read from a file instead of from standard input
  useful when piping
uniq  -> removes adjacent duplicated lines from its input
  uniq salmon.txt
$ sort salmon.txt | uniq
  combine with it in a pipe to remove all duplicated lines
$ cut -d , -f 2 animals.txt
  cuts first 2 elements in each line
$ cut -d, -f 2 animals.txt | sort | uniq -c
  produce a table that shows the total count of each type of animal in the file
$ ls *[AB].txt
  matches either an A or a B
$ rm *.txt
  remove all the processed data files
  raw files end in .dat and the processed files end in .txt

Loops

