# Scripting 
## basis
start script altijd met shebang

Bash gebruiken
```sh
#! /usr/bin/bash

echo "hello $[USER]"      
# Enkele aanhalingstekens kan je ook gebruiken bij echo maar deze gaan dan $[USER] letterlijk afdrukken

var="world"
printf 'Hello %s\n' "${var}"
```
Python gebruiken
```sh
#! bin/bash/python
print ("Hello world")
```


| Bescrijving| Commando|
|---|---|
| Geef alle vaiabelen in deze environment| `env`|

