# Jak používat GIT

Účelem tohoto jednoduchého návodu je ukázat, jak začít používat GIT. Tento návod
není vyčerpávající. Cílem návodu poskytnout rychlý úvod začátečníkům.

## Práce s repozitářem

Pokud čtete tento návod, tak vám zřejmě není cizí pojem softwarový projekt a 
pravděpodobně na nějakém i pracujete. Pro naše demonstrační účely si nyní 
jeden takový jednoduchý projekt vytvoříme.
 
* Obvyklým způsobem si vytvořte adresář TestProject
* V adresáři si vytvořte soubor main.c
* Soubor main.c otevřete ve svém oblíbeném editoru a zkopírujte do něj 
následující kód:

```c
#include <stdio.h>

int main(void) {
        puts("Hello World!");
        return 0;
}
```

Tak a máme jednoduchý projekt. Abychom s ním mohli pracovat v GITu, tak z něj
musíme udělat repozitář. Repozitář je projekt, který obsahuje metadata GITu 
(obvykle ve skrytém adresáři .git). Náš projekt převedeme na repozitář GITu 
následujícím způsobem:

* Pokud pracujete ve Windows, tak klikněte do adresáře pravým tlačítkem myši a
zvolte `Git Bash Here`. Otevře se vám příkazová řádka bashe.
* Napište následující příkaz, který inicializuje repozitář:

```
git init
```

Pokud vše proběhlo správně, tak byste měli v adresáři projektu vidět skrytý 
adresář .git. Pro kontrolu stavu v jakém se repozitář nachází napište:

```
git status
```

Měli byste vidět červený text main.c. To znamená, že v repozitáři je soubor,
který je nový, nebo obsahuje změny. Pokud byste soubor zkompilovali, tak by 
adresář obsahoval i soubor main.exe, který ale nebudeme chtít verzovat a tak 
by nám mohl překážet až bychom ho jednou omylem zaverzovali. Abychom se vyhnuli
podobným nepříjemnostem, tak je vhodné vytvořit v repozitáři soubor `.gitignore`
který bude obsahovat masku (masky) souborů, které se v projektu mohou nacházet,
ale my je nebudeme chtít nikdy zahrnout do verzí. Vytvořte tedy ve svém 
oblíbeném editoru soubor `.gitignore` a zkopírujte do něj následující obsah.

```
*~
*.o
*.obj
*.exe
*.res
```

Nyní když spustíme opět příkaz `git status` (v bash příkazovém řádku stačí 
nalistovat předchozí příkaz šipkou nahoru), tak vidíme dva červené soubory: 
main.c a .gitignore. GIT nám říká, že máme tyto 2 nové nebo změněné soubory
a očekává co snima chceme dělat dál.

* Nyní vybereme soubory, které budeme chtít commitnout (dáme je do takzvané 
stage)

```
git add main.c
git add .gitignore
```

* Pokud je modifikovaných souborů více a nechceme je přidávat po jednom tak:
 
```
git add .
```

Nyní když zkontrolujeme status repozitáře příkazem `git status`, tak vidíme
naše 2 soubory vypsané zeleně. To znamená že jsou vybrané ve stage a připravené
pro commit. Commit provedeme následujícím příkazem.

```
git commit -m "Pridal jsem dva soubory"
```

Nyní když zkontrolujeme status repozitáře příkazem `git status`, tak nám řekne,
že neexistují žádné změny. Historii commitů zobrazíme následujícím příkazem.

```
git log
```

Nebo pokud chceme vidět které soubory v commitech byly modifikovány.

```
git log --stat
```

Pokud nyní v souboru main.c uděláme nějakou změnu, tak nám ho `git status` opět
vypíše červeně. Pokud budeme chtít vidět co přesně jsme udělali za změnu, tak 
můžeme zkusit následující příkaz.

```
git diff
```

Nyní se můžeme rozhodnout zda chceme změnu zrušit a vrátit se k poslední 
commitované verzi. To bychom provedli následujícím příkazem.

```
git checkout .
```

Nebo zda chceme změnu potvrdit a commitnout. To provedeme nám už známou 
posloupností příkazů `git add .` a `git commit -m "commit message"`

## Jak dál

Nyní jsme zvládli nejzákladnější operace pro práci s GITem. S těmito příkazy si
pravděpodobně nějakou chvilku vystačíte. Pro další studium si můžete stáhnout 
[český překlad vynikající knihy Pro GIT](https://knihy.nic.cz/files/edice/pro_git.pdf). 
Mějte na paměti že: "VODU SÍTEM NABÍRÁ, KDO DO KNIH SE NEDÍVÁ".  
  
  

Váš projekt, nyní můžete [publikovat na GitHubu](HowToPublishOnGitHub.md).
