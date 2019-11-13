---
author: admin
comments: true
date: 2019-05-08 16:59:15+00:00
layout: post
link: https://chaitanyarahalkar.000webhostapp.com/path-environment-variable-in-linux-unix/
slug: path-environment-variable-in-linux-unix
title: PATH Environment Variable in Linux/Unix
wordpress_id: 76
categories:
- Linux
tags:
- environmentvariables
- linux
- path
- unix
---

##### What is the $PATH environment variable?

Every Linux & Unix System has several environment variables which are dynamic variables essential for running several processes in the system.
$HOME,$env being some of the well known environment variables.

The $PATH environment variable stores all the paths where one can find the binary executables for all the commands that we use.

Whenever a command is invoked from the terminal,all the paths in the $PATH environment variable are looked up and if the binary is found, the command is executed.

Trying this out on the terminal produces:

```bash
    echo $PATH
    
    /home/linus/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

```

The path variable can be usually edited or updated from the .bash_profile hidden file(On Unix like OS) or directly by exporting the variable with the export command.

Creating your own command recipies

Linux or Unix commands can be usually built by shell scripts, Python or Perl scripts.
Let us create a simple Bash script that calculates the factorial of the number sent to it as an argument in the command.

```bash  

    #!/bin/bash
    count=$1 
    fact=1
    while [ $count -gt 0 ] 
    do
       fact=$(( $fact * $count ))
       count=$(( $count - 1 ))
    done
    echo $fact
    
```

Create a sample file with a  .sh extension and copy the factorial code as given above.
Add the directory which contains the given file to your $PATH variable. Edit the variable from your .bash_profile or .profile located in your root directory with your preferred text editor.


```bash

    nano ~/.bash_profle
```

The file may contain several other aliases and variables but look out for the lines and update 
as shown below
(Make sure there are no spacings between PATH and =)



```bash

    export PATH=/home/linus/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/directory_of_bash_script
    
```
Do not forget to source the .bash_profile or .profile file with the source command or .


```bash
    
    source .bash_profile
```

Calling the script file name from the terminal with any number as the argument to the command will print the factorial to stdout.
The same thing can also be done by creating a symbolic link which will be discussed later.




