# Jak si nainstalovat GIT

Účelem tohoto jednoduchého návodu je ukázat, jak si stáhnout a nainstalovat GIT
v systémech Windows a Linux.

## Ve Windows

Stáhněte si instalaci GITu ze stránek https://git-scm.com/downloads
Spusťte instalaci a ponechte během instalace defaultní hodnoty.

## V Linuxu

V Linuxu je obvykle nejlepší volbou instalovat GIT z repozitáře dané distribuce.
V systémech odvozených od Debianu například příkazem:

```
$ apt-get install git
```

případně

```
$ sudo apt-get install git
```

## Konfigurace GITu po instalaci

Po instalaci GITu je potřeba nastavit některé parametry jako jsou:

* Vaše jméno nebo přezdívka, které budou použity, když budete commitovat změny
* Váš e-mail (například GitHub identifikuje uživatele právě podle e-mailu)
* Případně další parametry jako je třeba nastavení proxy

Pokud používáte Windows, tak otevřete průzkumník, klikněte pravým tlačítkem
myši někam do adresáře a z kontextové nabídky zvolte `Git Bash Here`.
Otevře se vám příkazový řádek typu bash. Příjemnou vlastností tohoto řádku je,
že nemusíte psát stejné příkazy opakovaně, ale šipkou nahoru můžete vybírat
z historie některý z předchozích příkazů a ten můžete i upravit. 

### Nastavení jména nebo přezdívky
```
git config --global user.name "Your Name"
```

### Nastavení e-mailu
```
git config --global user.email "you@example.com"
```

### Pokud používáte proxy
```
git config --global http.proxy http://proxyuser:proxypwd@10.0.127.41:8888
```

### Aktuální nastavení si můžete zkontrolovat následujícím příkazem
```
git config --list
```
