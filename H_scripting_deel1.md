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
 
 ## basic shelscript fouten opsporen
 ```sh
 
 set -o nounset       #foutmedling: x variebele is niet ingevuld maar wel gebruikt. deze gaat je verwittgen als er een vaiabele gebruikt wordt die niet bestaat, anders zou deze gwn een lege variabele gebruiken die niet gedefinieerd is
 
 set -o errexit     # gaat het script stoppen vanaf dat er een commando faalt (exitstatus 0 = commando geslaagd)
 set -o pipefail    # gaat ervoor zorgen dat je beter kunt achterhalen waar je pipes fout zijn als je pipelines gebruikt
 
```

## Scope van vaiabelen
variabelen zijn enkel te zien binnen de huidige omgeving en niet in de een subshell.

Globale/omgevingsvariabelen variabele maken kan je doen aan de hand van `export variabelken`

 DETAIL** Lokale variabelen worden geschreven in kleine letters. Omgeveringvariabelen worden geschreven in grote letters.

| Bescrijving| Commando|
|---|---|
| Geef alle vaiabelen in deze environment| `env`|
|boomstrctuur van alle processen dat op het systeem aan het lopen zijn| `pstree`|
| Toont hoe (veel shells) diep je zit| `echo ${SHLVL}` |




