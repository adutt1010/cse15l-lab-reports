### Lab report 1:

## cd:

![Image](report1cd.png)
The first time the `cd` command was run, it set the directory as `/home`, which is shown when I used the command `pwd`. Since there are no arguments it sets the directory to `/home` which is the default directory. In this case the directory didn't change because we were already in `/home`, but if we were in another directory and entered `cd`, it would've set the directory as `/home`.

The second time I ran the `cd` command with an argument `lecture1/messages`,which is the path to the messages directory, and it set the directory to `home/lecture1/messages`. The reason it set the directory to the argument I inputted, is because when I ran `cd`, it checked the argument I entered and chose the directory according to that, so it first checked if directory `/lecture1` exists, and then checked if `/messages` exists in `/lecture1`, and after that it set the directory to the `/lecture/messages`.  

The third time I ran the `cd` command with an argument of the `fr.txt` file located in the `/messages` directory, it gave us an error, as a file cannot be a directory. The directory did not change after running the command the third time, because previous argument was a filename, and as a result the directory is still `home/lecture1/messages`. So if you enter a filename as an argument to `cd`, it does not change the directory and gives us an error.


## ls:

![Image](15lLS.png)
The first time the `ls` command was run, it showed us the contents of the default directory that we were in, which is `/home`. The reason it shows us the contents of `/home` was because we entered no arguments and as a result it showed us the directory that were initially in. 

The second time the command was run, I entered a path to the directory `/lecture1` and it showed us the contents in that directory. The reason for this is beacuse I entered `/lecture1` as the argument and as a result it gave us the contents of `/lecture1`. It did not change the directory though which is shown when I ran `pwd` again.

The third time the command was run resulted in the terminal giving us the path to the file. The argument I gave was the path to the file `es-mx.txt`, and it gave us the path to just that file. The directory did not change when we ran that command, which is shown we run `pwd`.


## cat:

![Image](15Lcat.png)

The first time the `cat` command was run, nothing happened. I think it was expecting some input, so I pressed `ctrl+z` to exit the input part. I then checked the directory using `pwd` to see if anything had changed but we were in the `/home` directory.

The second time I ran it, I entered a path to the folder `/lecture1` and it told me that the input I had entered was a directory. I think the reason it gave this output was because it was expecting something else and was prompting me to give an appropriate input. The directory I was in still hadn't changed. 

The third time I ran it, I entered the path to the file `es-us.txt` as the argument, and it printed the contents of the file I entered. The directory did not change and remained home.
