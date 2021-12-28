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
|zoeken naar tekstpatronen in een bestand, zoek naar bert in deze file|`grep bert /etc/passwd`|



## oefening 
Toon welke commando's je het vaakst gebruikt (TOP10)  
```console 
history |awk '{ print $2}' | sort | uniq -c | sort -nr | head`
```
Zoek in een bestand naar alle regels die beginnen met een # (^ geeft aan in het het begin van een regel)  
```console 
grep '^#' script.sh
```
