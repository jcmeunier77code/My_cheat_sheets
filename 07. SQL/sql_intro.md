# SQL & PopSQL

## Cheat sheets 

<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/07.%20SQL/SQL-Cheet-Sheet-1.png"></p>
<p align="center" font-size="20px">Figure 1. Cheat sheet 1</p>

<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/07.%20SQL/SQL-Cheet-Sheet-2.png"></p>
<p align="center" font-size="20px">Figure 2. Cheat sheet 2</p>

<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/07.%20SQL/SQL-Cheet-Sheet-2.png"></p>
<p align="center" font-size="20px">Figure 3. Cheat sheet 3</p>


## Type of variables 

<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/img/sql_var.png"></p>
<p align="center" font-size="20px">Figure 4. Type of SQL variables</p>


```Shell 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install git
```

## Link git to your Github account

### Create a SSH key
To login into github you need a **SSH-key**. Here is how to generate one.

1. Create an SSH key linked to your email.

```console
me@laptop:~$ ssh-keygen -t ed25519 -C "your_email@example.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/*user_name*/.ssh/id_ed25519):
Created directory '/c/Users/*user_name*/.ssh'.
```
OR
```console
me@laptop:~$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

