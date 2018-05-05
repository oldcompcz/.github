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

* Na stránce HitHubu vpravo nahoře klikneme na ikonu + a zvolíme 
`New repository`
* Zvolíme název "TestProject" a popis. Repozitář zvolíme veřejný a potvrdíme.
* Repozitář je založený a GitHub nám napovídá jak můžeme pokračovat.

Přepneme se do projektu na počítači. Pokud pracujete ve Windows, tak klikněte do
adresáře pravým tlačítkem myši azvolte `Git Bash Here`. Otevře se vám příkazová 
řádka bashe. Nastavíme cestu ke vzdálenému repozitáři a pushneme projekt na 
server.

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

## Vytváření release

## Issues

## Pull requesty

## Jak dál
