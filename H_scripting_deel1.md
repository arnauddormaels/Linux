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
Variabelen in bash
```sh
 #/usr/bin/bash

User=bob  #opgepast gen spaties rond '=' anders denkt het sccript dat je een methode wilt oproepen 
 
touch "${bestand}"  #altijd dubbele aanhalingstekeens gebruiken bij het oproeen van een variabele 
 ```
 
 
 ```sh
 
 set -o nounset       #foutmedling: x variebele is niet ingevuld maar wel gebruikt. deze gaat je verwittgen als er een vaiabele gebruikt wordt die niet bestaat, anders zou deze gwn een lege variabele gebruiken die niet gedefinieerd is
 
 set -o errexit     # gaat het script stoppen vanaf dat er een commando faalt (exitstatus 0 = commando geslaagd)
 set -o pipefail    # gaat ervoor zorgen dat je beter kunt achterhalen waar je pipes fout zijn als je pipelines gebruikt
 

| Bescrijving| Commando|
|---|---|
| Geef alle vaiabelen in deze environment| `env`|

