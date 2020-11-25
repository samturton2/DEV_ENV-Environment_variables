# Environment variables
These exist globally on a specific environment or machine.

Generally you dont want to have too many of them.

You can interpolate them into code and other services.

## Agenda

- What are variables vs environemtns variable in bash
- Process and child process
- default variables
- How to set the environment variables in bash

## Variables in bash

Generally you use uppercase and assing using no space followed by the string or process.
```bash
MY_VAR=hello
```

Read a variable using echo

![](img/ech.png)

These variables, are *NOT ENVIRONMENT VARIABLES* and exist only on the process and (the current terminal).

Once you restart the terminal or a new process these variables do not continue.

## Child processes

When your terminal runs another file or bash script it  makes a child process.

A child process is bassically a new terminal
### Export
Send variable to child process

You can use `export` to make a variable available to child process
```bash
export MY_VAR
./my_process.sh
> this is a line from my_process file
> hello
```
(still not permanent, when terminal restarted it will be lost)

### Checking the variables
`printenv`
`env`

## Making variables persistent in computor

The definative response lies in understanding how an individuals terminals are created. 

The PATH taken. 

Each individual terminal has a path to conclude before opening for you to use it. 

To set an environment variable: you are going to write in one of the files that it reads as it does it's PATH.

You want to have this in .profile
```bash
#if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrfc if it exists
    if [ -f "&HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi
```

And then you can write in .bashrc your variables 
