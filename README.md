# GenBank-dataset modifications

This file is the raw file dowloaded from GenBank. https://www.ncbi.nlm.nih.gov/genbank/
* Search for "levansucrase" in the PROTEIN database and select from BACTERIA and REFSEQ.
* Send to file: Choose--> FASTA

Why do I need to modify this file?

I want a file that looks like this:
```
>WP_127776368.1 glycoside hydrolase family 68 protein [[Brevibacterium] frigoritolerans]
MNFSRLAKQATAGILSTGILLSGTVTQSFAAPKDPADYKETYDTSQITRSAMKDMINQHGDTRYAVPRFDESTIKNIPSAKKVTESGETIDLDVWDTWPLQNADGTVAEYKGYHIVFGLAGDPKNASDTFIYIFYKKVGDNSLDAWKNAGRVFDDNDKNVPNDPYLKEQAEEWSGSATFTEDGEVRLFYTNREPYIPESGNYGKQTLTTAQVNLSEPDSETLKVDGVEDYKSIYEGKDSKYYQTVDKFVEDGNSADNHTFRDPHYVEDNGRKYLVFEANTGTEYGYQGEESLYNRAYYGNSNKFFQAEKNKLMQSPKKELAELANGAIGIIEVNDDYTLKKEMKPLIVSNTVTDEIERPNIFKKDGKWYLFTSSRGSKMTIDGIDNQDIYMLGYTSNSLTGPYKPLNKTGIVLHQDLDPYDITWNYAHYAIPQAGSDNVVVTSYMTNRGYFEDNKSTFAPSFQLNIKGKNTSVVKDSILEQGQITVK
>WP_133313889.1 glycoside hydrolase family 68 protein [[Brevibacterium] frigoritolerans]
MNFSRLAKQATAVTLSTGILLSGTVTQSFAAPKDPADYKETYGTSQITRSAMKDMINQHGDARYTVPKFDESTIKNIPSAKKVTESGETIDLDVWDTWPLQNADGTVAEYNGYHIVFGLAGDPKNANDTFIYLFYKKAGDNSLDAWKNAGRVFDNNDKNVPNDPYLKHQAEEWSGSATFTEDGEVRLFYTNREPYTADTGHYGKQTLTTAQVNLSQPDSKTLKVDGVEDYKSIYEGKDSKYYQTVDKFVEDGAPSDNHTFRDPHYIEEDGRKYLVFEANTGTEYGYQGEESLYNQAYYGNSNKFFQEEKTKLLNSDKKQLAEVANGAIGIIEINDDYSLKKEMKPLIVSNTVTDEIERPNIFKKGGKWYLFTSSRGSKMTIDGMDNQDIYLLGYVSNSLTGDYKPLNKTGIVLHQDLDPNDITWNYAHYAIPQEGSDNTVVTSYMTNRGFFEDHKSTFAPSFKLNIKGDKTTVVKDSILEQGQITEK

```

BUt the file as it is, looks like this:
```
>WP_127776368.1 glycoside hydrolase family 68 protein [[Brevibacterium] frigoritolerans]
MNFSRLAKQATAGILSTGILLSGTVTQSFAAPKDPADYKETYDTSQITRSAMKDMINQHGDTRYAVPRFD
ESTIKNIPSAKKVTESGETIDLDVWDTWPLQNADGTVAEYKGYHIVFGLAGDPKNASDTFIYIFYKKVGD
NSLDAWKNAGRVFDDNDKNVPNDPYLKEQAEEWSGSATFTEDGEVRLFYTNREPYIPESGNYGKQTLTTA
QVNLSEPDSETLKVDGVEDYKSIYEGKDSKYYQTVDKFVEDGNSADNHTFRDPHYVEDNGRKYLVFEANT
GTEYGYQGEESLYNRAYYGNSNKFFQAEKNKLMQSPKKELAELANGAIGIIEVNDDYTLKKEMKPLIVSN
TVTDEIERPNIFKKDGKWYLFTSSRGSKMTIDGIDNQDIYMLGYTSNSLTGPYKPLNKTGIVLHQDLDPY
DITWNYAHYAIPQAGSDNVVVTSYMTNRGYFEDNKSTFAPSFQLNIKGKNTSVVKDSILEQGQITVK

>WP_133313889.1 glycoside hydrolase family 68 protein [[Brevibacterium] frigoritolerans]
MNFSRLAKQATAVTLSTGILLSGTVTQSFAAPKDPADYKETYGTSQITRSAMKDMINQHGDARYTVPKFD
ESTIKNIPSAKKVTESGETIDLDVWDTWPLQNADGTVAEYNGYHIVFGLAGDPKNANDTFIYLFYKKAGD
NSLDAWKNAGRVFDNNDKNVPNDPYLKHQAEEWSGSATFTEDGEVRLFYTNREPYTADTGHYGKQTLTTA
QVNLSQPDSKTLKVDGVEDYKSIYEGKDSKYYQTVDKFVEDGAPSDNHTFRDPHYIEEDGRKYLVFEANT
GTEYGYQGEESLYNQAYYGNSNKFFQEEKTKLLNSDKKQLAEVANGAIGIIEINDDYSLKKEMKPLIVSN
TVTDEIERPNIFKKGGKWYLFTSSRGSKMTIDGMDNQDIYLLGYVSNSLTGDYKPLNKTGIVLHQDLDPN
DITWNYAHYAIPQEGSDNTVVTSYMTNRGFFEDHKSTFAPSFKLNIKGDKTTVVKDSILEQGQITEK

```

I also want to remove all sequences that do not contain ***"levansucrase"***

## How to do get only one line sequences?
0) Open file w/ notepad+++
1) Change CRLF for LF. Go to Edit-->EOL conversion--> Unix
2) Replace. Type control H. Press Regular expression only. Do not match ". newline" 
3) Type in ***Find what:*** (^>.*)     /   ***Replace with:*** \1meloni1      

EXPLANATION:

```
FIRST STEP
Find what:
^           beginning of line
^>          line starts with >
^>.         line starts with > and follows any number
^>.*        line starts with > and follows any number any given times
(^>.*)      selets only this part but not the LF (\n) in the end


SECOND SETP
Replace with:
\1          Replace the Find what with exactly the same thing between ()

THIRD STEP
Replace with:
\1meloni1   replace the line with the exact same between () and add meloni1

```
4) Search for the line only containing LF and replace with meloni2--> 
```
Find what:
^\n    

Replace with:
meloni2

```
5) Delete all LF

```
Find what: 
\n    

Replace with: 
(nothing)

```
6) Replace meloni1 and meloni2 with \n
``` 
Find what:
meloni1  

Replace with:
\n 
```
7)Do the same with meloni 2.

DONE


