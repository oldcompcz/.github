# Jak publikovat GIT repozitář na GitHubu

Účelem tohoto jednoduchého návodu je ukázat, jak publikovat a pracovat s 
repozitářem na github.com.

## Proč publikovat projekt?

Cílem zveřejnění projektu na github.com je zejména:

* Vybudovat si komunitu uživatelů a poskytovat dokumentaci, informace o 
releasech a fixech.
* Spolupráce s dalšími vývojáři, kteří mohou do projektu přispívat.

GitHub umožňuje zdarma vytváření neomezeného množství veřejných repozitářů. 
Je rovněž možné vytvářet privátní repozitáře, které vidí jen vlastník a případně
omezená komunita vývojářů. Privátní repozitáře jsou ale na GitHubu zpoplatněny.  

Pokud je vaším cílem mít uzavřený projekt s omezenou skupinou vývojářů, tak je
zřejmě výhodnější využít služeb bitbucket.com. Je to server velmi podobný 
GitHubu, ale umožňuje založení a provoz privátních repozitářů s přístupem do
pěti vývojářů zdarma.

## Založení účtu na github.com

Pokud ještě nemáte založený účet, tak navštivte stránku github.com a založte si
ho. Ujistěte se, že ve svém profilu máte uvedený stejný mail, který jste si
nastavili při instalaci gitu na svůj počítač. Tento mail je součástí commit 
messages a github podle něj identifikuje uživatele, který commit provedl. Pokud
nenajde účet s příslušným mailem, tak nedokáže u commitů zobrazit správného
uživatele.

## Založení repozitáře na github.com a práce s ním

### Vypublikování repozitáře

Nyní máme účet na github.com a předpokládejme, že na svém počítači máme projekt
TestProject, který chceme zveřejnit na GitHubu.  

* Na stránce HitHubu vpravo nahoře klikneme na ikonu `+` a zvolíme 
`New repository`
* Zvolíme název "TestProject" a popis. Repozitář zvolíme veřejný a potvrdíme.
* Repozitář je založený a GitHub nám napovídá jak můžeme pokračovat.

Přepneme se do projektu na počítači. Pokud pracujete ve Windows, tak klikněte do
adresáře pravým tlačítkem myši azvolte `Git Bash Here`. Otevře se vám příkazová 
řádka bashe. Nastavíme cestu ke vzdálenému repozitáři a pushneme projekt na 
server. (myuser v adrese nahraďte svým přihlašovacím jménem)

```
git remote add origin https://github.com/myuser/TestProject.git
git push -u origin master
```

Nyní máme lokální projek vypublikovaný a propojený se vzdáleným repozitářem na 
GitHubu.

### Klonování repozitáře

Pokud si sedneme k jinému počítači, kde projekt nemáme a chtěli bychom si ho 
stáhnout (naklonovat), tak to provedeme následujícím příkazem

```
git clone https://github.com/myuser/TestProject.git 
```

### Lokálni versus vzdálený repozitář

Další práce na projektu je podobná jako když jsme měli pouze lokální repozitář
na počítači. V projektu provádíme změny, změněné soubory přidáváme do stage a 
commitujeme tak jak jsme zvyklí `git add .`, `git commit -m "Commit message"`.  

Pokud chceme naše lokální commity poslat na server, tak nejprve stáhneme 
případné změny ze vzdáleného serveru k sobě.

```
git pull
```

Pokud nějaké vzdálené změny byly, tak se provede merge. Následně můžeme naše 
změny poslat na server.

```
git push
```   

## Read me

V žádném projektu by něměl chybět read me soubor, kde byste měli napsat základní
informace o projektu. Minimálně by měl read me obsahovat jak projekt stáhnout, 
sestavit a spustit, případně také popis použití.  

Read me soubror může být buď klasický textový `README.txt` nebo modernější, 
formátovaný ve značkovacím jazyce Mark Down `README.md`. Přehled značek 
Mark Down naleznete 
[zde](https://guides.github.com/features/mastering-markdown/).
Pokud máte rádi emotikony, tak si v Mark Down také 
[přijdete na své] (https://www.webpagefx.com/tools/emoji-cheat-sheet/).  

Mark Down je na GitHubu preferovaný a lze ho používat všude kde něco píšete. 
V issues, v komentářích ale třeba i v informacích o sobě ve svém profilu. 

## Vytváření release

V každém projektu jednou za čas dojdete do fáze, kdy si řeknete, že byl učiněn 
dostatečný pokrok a zároveň je nyní program stabilní a mohli byste tedy nyní
vydat nový release. Vydat na GitHubu release je jednoduché a používají se
pro tento účel takzvané tagy.  

Přepneme se do projektu na počítači. Pokud pracujete ve Windows, tak klikněte do
adresáře pravým tlačítkem myši azvolte `Git Bash Here`. Otevře se vám příkazová 
řádka bashe. Následujícím příkazem si vylistujeme seznam už existujících tagů v
našem projektu. Nyní tam zřejmě žádné nebudou.

```
git tag
```

Vytvoříme tedy nový tag Release 1.0.0. První číslice je tzv. major číslo, které
se mění když byla v projektu nějaká velmi zásadní změna. Druhé číslo verze je
tzv. minor číslo, které budeme měnit, když přibylo několik vlastností. Poslední
číslo je tzv. revize, nebo číslo buildu. Obvykle se mění když jsme jen 
zafixovaly nějaké chyby.

```
git tag "Release 1.0.0"
```

Zkontrolujeme nyní zda se nám tag v projektu vytvořil `git tag` a můžeme ho 
vypublikovat na GitHub.

```
git push origin "Release 1.0.0"
```

Když se přepnete v prohlížeči do svého projektu na GitHubu, tak v horní liště 
projektu uvidíte `1 release`. Klikněte na něj a uvidíte svůj tag. Vpravo nahoře
je tlačítko `Draft a new release`. Když na něj kliknete, tak můžete vytvořit 
popis release. Vyberte tag, který reprezentuje release a vyplňte release title.
Následně můžete napsat lbovolné informace o release. Je možné používat Mark 
Down. Zároveň můžete k release přiložit zkompilované binárky. Ty nebudou 
součástí repozitáře, ale GitHub je bude nabízet uživetelům ke stažení v sekci
releases. Nakonec vše potvrďte talčítkem `Publish release`. 

## Issues

## Pull requesty

## Jak dál
