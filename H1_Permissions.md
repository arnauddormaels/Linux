# Octale notatie

r(read) = 4
w(write) = 2
x(excecute) = 1
U(ser)-G(roup)-O(thers)
a(all)


voorbeeld `chmod 755 script.sh`
Extra**  
max octale notatie voor directory is 666 (een dir kan je niet excecuten)
max octale notatie voor file is 777 

# normale permissie

| Beschrijving   |  code |
|---|---|
|Permissies toevoegen |  `   chmod g+rw `| 
| Permissies afnemen  | `chmod g-rw`  | 
| permissies overal hetzelfde maken  | `chmod a=r`  | 


# Umask 
-> bepaalt de permissies van nieuwe bestanden/directories. De waarde van de umask bepaald welke permissies afgenomen worden (omgekeerde van de octale notatie). 
Berekenen: max (666/777) - umask(vb 033) = nieuwe default permissie (744)


# SPeciale permissies 
## SUID (set user ID)
- werkt enkel op files met excecute permissies 
- Vervangt de x bij user permissies door een s `-rws-r-xr-x` 
- Als de Other een excecute permissie heeft dan krijgt deze aan de hand van de bovenstaande permissie de  dezelfde permissies als de eigenaar van het bestand. Op deze manier kan een gebruiker bv heel even root worden als root de eigenaar is van deze file.
- commando `chmod u+s` of `chmod 2777` (2 staat voor SGID)

niet vergeten x moet aanstaan bij Others

## SGID (Set Group ID)
- Heeft dezelfde regels als de SUID 
- Vervang de X bij de group permissies door een s `-rwx-rwsr-x`
- Gebruiker krijgt zelfde rechten als de group van de eigenaar ook al zit deze niet in dezelfde group. 
- commando `chmod g+s`of `chmod 4777` (4 staat voor SGID) 

niet vergeten x moet aanstaan bij Others

## Restrcted deletion
- Sticky bit 
- Zo zou het eruit moeten zien ('t' is sticky bit)`drwxrwx rwt`
- enkel de eigenaar kan bestanden verwijderen in deze directory.
- commando `chmod +t` of `chmod 1777` (de 1 staat voor restricted deletion/de sticky bit).

TIP** voor enkel de permissie te tonen van de directory `ls -ld dirTemp` anders zie je atlijd permissies van de files die in de directory zitten en niet die van de directory zelf. Je kan ook altijd naar de dir erboven gaan om dan de permissies van de temp dir te bekijken (als dat makkelijker is).


# Extra informatie

/etc/shadow -> bevat de wachtwoorden (encrypted) van alle gebruikers (enkel de root kan deze openen)

/etc/shadow -> bevat de wachtwoorden (not encypted)

`cat /etc/passwd` -> inhoud van het bestand afdrukken

`touch bestandTemp` -> maakt nieuw tekst bestand aan

`sudo !!` -> gaat het vorige commando opnieuw uitvoeren (handig voor als je sudo was vergeten te typpen)


# Beheren van gebruikers 
- users `useradd`, `usermod`, `userdel`
- groups `groupadd`, `groupmod`, `groupdel`
- Info opvragen `who`, `groups`,`id`

|Beschrijving| Commando |
|---|---|
|maakt een nieuwe gebruiker bert (moet met sudo want enkel de root kan gebruikers aanmaken)|`sudo adduser bert`|
| Toont bestand waar gebruikers worden bijghouden | `less /etc/passwd` of `vim /etc/passwd`(geeft hetzelfde maar met mooie kleurtjes, dit instaleren staat in colgende commando) |
| instaleer vim | `sudo apt install vim`|
| Toont alle groups (gebruiker wordt niet vermeld in zijn eigen primaire group vb user=bert group=bert dit kan je enkel zien in /etc/passwd)| `vim /etc/group` |
| Primaire groep veranderen | `sudo usermod -g groepsken jan` |
| groep veranderen, de gebruiker zit enkel in deze groepen vanaf nu | `sudo usermod -G groep1,groep2 jan`|
| groep toevoegen aan de gebruiker | `sudo usermod -aG groep3 jan`|
| Toont welke gebruiker je bent | `who`|
| Toont tot welke groepen je behoort | `group`|
| Geeft alle informatie over de gebgruiker| `id jan`|
| Eigenaar van een file veranderen | `sudo chown jan bestand` |
| Eigenaar en group aanpassen van een file| `sudo chown jan:groepsken bestand`|
| Enkel group aanpassen | `chgrp groepsken bestand `|
| inloggen als een andere gebruiker | `su - jan`|
| uitloggen kan via 2 manieren | `logout` of CRTL D|
| | |
| Gebruiker correct aanmaken |
| | |
| | |
| | |








