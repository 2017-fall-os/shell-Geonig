# os-shell

Operating systems shell lab

## Description of shell 

This is a basic shell that uses execve to run programs and access programs. 
Its based on a shell developed by Stephen Brennan and his tutorial on building a shell which you can find here.
https://brennan.io/2015/01/16/write-a-shell-in-c/
https://github.com/brenns10/lsh

Main: Calls the method getPaths and stores it in an double pointer of chars. 
Then calls the lsh_loop and passes the envp and the newly created double pointer char. 

lsh_loop: This is the main method used to create and pass the arguments needed to run commands. 
It has a do while loop which gets user input via the lsh_read_line call and stores it in a char pointer. 
The char pointer is then passed into the mytoken function stored in the tokenizer file and returns 
a double pointer of chars seperated by spaces. Next is lsh_execute which return a int and takes the args and paths and envp.
It's value is stored in status which determines the conditions for the do while.Then finally frees the 
space for the line and args. 

lsh_read_line: allocates space for a buffer for input. Reads the input and store the results in a char pointer that is returned. 

myToken: Tokenizer used from mytok. that returns a double char pointer. 

lsh_execute: Takes 3 parameters. a list of tokenized commands, a list of the paths, and envp (enviorment varibles). 
Checks if the list is empty and returns 1 if it is. Then checks if the arguments passed are apart of the built in commands
using the compareStr call. If it is it executes it. If its no it passes it to Lsh_launch. 

Lsh_launch: Takes the same 3 parameters as lsh_excute. Then forks from the current process. Attepmts to execve the commands and store the results 
in a varriable named success. Otherwise it uses a for loop to search for the proper path. 
