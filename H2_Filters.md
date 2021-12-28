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
| gaat de file afprinten|`cat file `||
| gaat de file afprinten in omgekeerde volgorde|`tac file`||
| gaat de file apfrinten in willekeurige volgorde|` shuf file`||
| toont de eerste 10 regels van de file|`head file`||
| toont de laatste 10 regels van de file,|`tail file`| `-f` de file blijft openstaan en gaat ook afprinten als er achteraf nog iets bijkomt| 
