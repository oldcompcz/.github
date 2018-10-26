# Podepisujte své commity pomocí PGP klíče

Git vás po nainstalování vyzve k zadání vašeho jména a e-mailu a tyto údaje pak používá v každém vašem commitu. Problém je, že si jméno i e-mail můžete zcela vymyslet, nebo se vydávat za někoho jiného. Proto existuje možnost své commity podepisovat. Github pak bude u vašich commitů ukazovat tag Verified s vaší digitální identitou.  

Cílem tohoto návodu je ukázat, jak můžete své commity podepisovat pomocí svého osobního PGP klíče.

## Vytvoření osobního PGP klíče a nastavení automatického podepisování commitů

1. Vygenerujte si PGP klíč pokud ho ještě nemáte `gpg --gen-key` a uveďte svůj v githubu ověřený e-mail.
1. Vypište si seznam klíčů `gpg --list-keys` a vyexportujte si svůj veřejný klíč do souboru `gpg --armor --export <keyid> > mykey.pub`
1. Vložte si svůj veřejný klíč do profilu v GitHubu (Settings - SSH and GPG keys)
1. Nastavte si v gitu na počítači aby automaticky všechny commity podepisoval `git config --global commit.gpgsign true`. Pokud máte více klíčů tak můžete zvolit aby git používal jeden konkrétní `git config --global user.signingkey <keyid>`.

To je celé.

## Key signing

Pro zvýšení důvěryhodnosti svého klíče si můžete nechat svůj veřejný klíč podepsat někým kdo vás zná. Případně můžete navštívit některou Key Signing Party - například na [LinuxDays](https://www.linuxdays.cz/). Na key signing party se sejdou lidé, kteří si navzájem ověří identitu a podepíší si vzájemě své pgp klíče.   

Pokud tam vyrazíte tak si:

1. předem svůj veřejný klíč nahrajte na pgp server `gpg --keyserver pool.sks-keyservers.net --send-keys <keyid>` (propsání takto exportovaného klíče na všechny servery může nějakou dobu trvat).
1. vytiskněte si lístečky se svým veřejným klíčem, které si na párty vyměníte s ostatníma http://openpgp.quelltextlich.at/slip.html

Více o KSP a podepissování klíčů naleznete třeba zde: https://www.linuxdays.cz/2017/key-signing-party/

## Šifrování souborů pomocí PGP

Nástoj PGP používá pár klíčů - veřejný a privátní. Veřejný klíč můžete nahrát na server, a tím ho zveřejnit pro ostatní `gpg --keyserver pool.sks-keyservers.net --send-keys <keyid>`. Privátní klíč si naopak držíte v bezpečí u sebe a dobře si ho zazálohujete.  

Pokud chcete někomu poslat soubor s citlivým obsahem:

1. Je třeba mít veřejný klíč příjemce. Buď vám příjemce sdělí fingerprint svého klíče, nebo můžete zkusit vyhledávat podle mailové adresy nebo jména třeba zde http://openpgp.quelltextlich.at/slip.html Jakmile máme keyid nebo fingerprint veřejného klíče příjemce, tak si ho stáhneme k sobě do počítače `gpg --keyserver pool.sks-keyservers.net --recv-keys <keyid>`. 
1. Soubor zašifrujete příkazem `gpg -ear <keyid> <soubor>`, kde místo keyid veřejného klíče můžete použít jen jméno nebo příjmení příjemce uvedené v jeho veřejném klíči. Takto zašifrovaný soubor bude moci dešifrovat jen majitel privátního klíče patřícího do páru s použitým veřejným klíčem.
1. Příjemce soubor jednoduše dešifrune příkazem `gpg -d sifrovany_soubor > desifrovany_soubor`

Takto je možné zašifrovat třeba velký soubor a nahrát ho na ulozto.cz. K obsahu souboru se pak dostane jen majitel příslušného privátního klíče.  

Tip: vložte si do podpisu e-mailu fingerprint svého veřejného klíče, aby ho vaši kolegové a známí snadno našli. Fingerprint svého klíče získáte příkazem `gpg --fingerprint <keyid>`

## Jak dál
 
Dále můžete pokračovat návodem [Jak si nastavit protokol SSH](HowToUseSsh.md).
