# Jak si nastavit protokol SSH

Cílem návodu je ukázat jak si nastavit a jak používat protokol ssh.

## Vygenerování klíče a nastavení profilu

1. Vygenerujte si pár soukromého a veřejného klíče. Spusťte příkaz: `ssh-keygen` Ve vašm profilu v adresáři .ssh se vytvoří id_rsa (soukromý klíč) a id_rsa.pub (veřejný klíč)
1. Vložte si svůj veřejný klíč (id_rsa.pub) do profilu v GitHubu (Settings - SSH and GPG keys)
1. Nyní si můžete naklonovat svůj projekt pomocí protokolu ssh: `git clone git@github.com:myprofile/myproject.git`

## Pokud chcete aby si počítač pamatoval heslo k privátnímu klíči

Spusťe následující dva příkazy. Počítač se vás zeptá na heslo a bude si ho po celou dobu práce pamatovat. 

```sh
eval $(ssh-agent)
ssh-add
```
