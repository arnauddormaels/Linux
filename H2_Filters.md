# Filters
## Wat doet een filter filter
- 1 leest **stdin** of een bestand
- 2 tekst transformeren
- 3 schrifjt tekst weg naar **stdout**  

Je kan filters ook combineren adhv pipelines |

```console 
filter file1 file2...
filter < file
cmd | filter

```

|Bescrhrijving| Commando | mod|
|---|---|---|
| gaat de file afprinten|`cat file `|
| gaat de file afprinten in omgekeerde volgorde|`tac file`|
| gaat de file apfrinten in willekeurige volgorde|` shuf file`|
| toont de eerste 10 regels van de file|`head file`|
| toont de laatste 10 regels van de file,|`tail file`| `-f` de file blijft openstaan en gaat ook afprinten als er achteraf nog iets bijkomt| 
| hiermee kan je kolommen selecteren, elke rij is een record, elke record is verdeeld in kolommen deze onderscheiden door een TAB|`cut file -f1,3-5`| `-d:` gaat : nenem als karakter voor de kolommen te scheiden ipv TAB|
|bestand regels gaan samenvoegen in text.txt|`paste -d, text.txt password.txt`|`-d,` gaat ervoor zorgen dat deze samengevogde regels gescheiden worden door komma's|
| 5 regels van willekeurige wachtwoorden generren|`apg -n 5`|
|ongesorteerd bestand regel per regel sorteren |`sort file `| `-t:` aangeven dat het bestand is opgespllits in dubbele punten <br>`-k 3` sorteren volgens 3e kolom <br>`-n` nummeriek sorteren, anders gaat die getallen ook alfabetisch willen sorteren <br> `r` reverse, volgorde omdraaien (van klein naar groot)|
|gaat alle dubbelle lijnen uit de file halen| `uniq file`|`-c` (count) Gaat tellen hoevaak elke lijn voorkomt|
|Toont welke commando's dat je gebruikt hebt| `history`|
| tekst opmaak aanpassen | `fmt -w100 file`|`-w100` gaat de regels 100 karakters lang maken|
| Gaat regelnummers toevoegen (enkel de regels waar tekst op staat, lege regels krijgen geen nummer)|`nl file`|
| geeft het aantal regels, aantal woorden, aantal karakters in deze voglorde|`wc file`|`-w` geef enkel het andere woorden <br> `-c` karakcters <br> `-l` aantal lijnen|
|zoeken naar tekstpatronen in een bestand, zoek naar bert in deze file|`grep bert /etc/passwd `| `-i` case insensetive zoeken|
| Karakters systematisch omzetten naar andere karakters ,elk teken in het eerste deel wordt vervangen door het karakter in het 2e deel | `tr 'A-Z' 'a-z < UPPERCASE.txt > lowercase.txt`| het eerste > is voor iets parsing omdat je anders geen file zou kunnen doorgeven?<br> `-d [:punct:]` gaat alle dubbele punten,slashes en komma's verwijderen|


## Sed commando
sed dient om het zoekn en vervangen stukjes regels. En maakt gebruik van regex(handig om is op te zoeken voor beter te begrijpen wat je kunt doen met sed), reguliere expressies. 
```console 
sed 's/aba/aka'
```
- s staat voor substitute (vervangen)
- het eerste deel "aba" gaan we zoeken in elke regel en vervangen door het 2e deel "aka", dit gaan we maar 1 keer doen per regel.

```console 
sed 's/aba/aka/g'
```
- /g gaat ervoor zorgen dat we aba meerdere keren kunnen vervangen per regel

```console 
sed '/^#/d'
```
- /d staat voor delete regel
- ^ staat voor begin van de regel
- we gaan elke regel die begint met een # verwijderen

```console 
sed '/^$/d'
```
- $ staat voor het einde van de regel
- dus als het begin van de regel en het einde van de regel na elkaar komen betekent dit dat de regel leeg is
- verwijdert alle lege lijnen

## awk commando 
Wat tussen de accolades staat wordt uitgevoerd op elke regel
```console 
awk '{ print $4} file'
```
- gaat de 4de kolom afdukken voor elke regel
- kolommen worden gescheiden door witruimte

```console 
awk -F: '{ print $4} /etc/passwd'
```
- `-F:` aangeven dat de kolommen gescheiden zijn door ":"
- gaat de 4e kolom afdrukken voor elke regel 

```console 
awk -F: '{ print $1 ":" $4} /etc/passwd'
```
- `-F:` aangeven dat de kolommen gescheiden zijn door ":"
- gaat de 1e en 4 kolommen voor elke regel afdrukken gescheiden door een ":"

```console 
awk -F: ' /^b/ { print $1 ":" $4} /etc/passwd'
```
- print enkel de kolommen waarvan de regel begint met een b
```console 
awk -F: ' /bash$/ { print $1 ":" $4} /etc/passwd'
```
- print enkel de kolommen waarvan de regel eindigt op bash

```console 
awk -F: ' { if ($3 > 1000) print $1 ":" $3} /etc/passwd'
```
- print enkel de lijnen waarvan kolom 3 groter is dan 1000


## oefening 
Toon welke commando's je het vaakst gebruikt (TOP10)  
```console 
history |awk '{ print $2}' | sort | uniq -c | sort -nr | head`
```
Zoek in een bestand naar alle regels die beginnen met een # (^ geeft aan in het het begin van een regel)  
```console 
grep '^#' script.sh
```

# I/O Redirections
| beshcrijving | commando| mod|
|---|---|---|
| shcrijf uitvoer van cmd naar de file| `cmd > file`| - `>>` :voeg toe aan einde van de file <br> - `2>`: schrijf de foutboodschap weg naar de file <br> - `<`: gebruik de inhoud van de file als invoer voor het commando|
| gebruikt de uitvoer van cmd1 als invoer van cmd 1, voorbeeld van een pipe|`cmd1 | cmd2`|
| gaat de files/directories zoeken adhv de parameters|`find / -type d`|- `/` zoeken vanaf de rood directory <br> -`-type d` geef de directories|
| Tekst wegschrijven als foutboodschap|`printf'Er is een foutje in dir %s' "${dir}" >&2`|


## here document 
handig voor meerdere lijnen te schrijven. Veel leesbaarder dan bv 10 echo's onder elkaar.
Je kan hier ook bv sql code in schrijven voor het te gebruiken in een sql script.
```console 
cat << EOF
de naam van de gebruiker is ${USER}
zijn id is ${ID}
EOF
```

# pipes

instaleer onderstaande custom code 
 
```console 
sudo apt install fortune cowsay lolcat figlet
```

probeer deze eens uit en probeer wat leuke combinaties uit aan de hand van pipes |, zoals 
``` echo ${USER| figlet
fortune
cowsay
lolcat
fortune | cowsay
fortune | cowsay | lolcat
```



