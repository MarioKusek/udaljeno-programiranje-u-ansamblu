# Udaljeno programiranje u ansamblu (*remote ensemble/mob programming*)

Sadržaj:
<!-- TOC -->

- [Udaljeno programiranje u ansamblu (*remote ensemble/mob programming*)](#udaljeno-programiranje-u-ansamblu-remote-ensemblemob-programming)
  - [Priprema za rad](#priprema-za-rad)
    - [Instalacija programa](#instalacija-programa)
    - [Github](#github)
  - [Uvod u programiranje u ansamblu](#uvod-u-programiranje-u-ansamblu)
    - [Organizacija](#organizacija)
    - [Uloge](#uloge)
    - [Okolina u kojoj radimo](#okolina-u-kojoj-radimo)
    - [Kako govoriti?](#kako-govoriti)
    - [Iskustva](#iskustva)
  - [Literatura](#literatura)

<!-- /TOC -->

## Priprema za rad

### Instalacija programa

- Java 11+ - [upute](https://www.fer.unizg.hr/_download/repository/01.1-Podesavanje_varijabli_okruzenja.pdf)
  - Windows: [JDK 15 General-Availability Release](https://jdk.java.net/15/)
  - Linux/Mac: [SdkMan](https://sdkman.io)
- Eclipse ili neki drugi IDE
- Git
  - Windows: [Git for Windows/Git bash](https://git-scm.com/download/win)
  - Linux/Mac - imaju instalirano
- Alat [Mob](https://mob.sh)
  - Windows: instalirati u Git Bashu
  - Linux/Mac: instalirati u terminalu
- MS Teams - instalirati ga

### Github

Ako nemate korisnički račun na GitHubu treba ga otvoriti ([upute za otvaranje računa](https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github/signing-up-for-a-new-github-account))

## Uvod u programiranje u ansamblu

Engleski nazivi:

- *Mob Programming* - popularan, ali ima negativnih konotacija
- *Enesemble Programming* - preporuča se jer nema negatinve konotacije

### Organizacija

- timovi su veličine od 3-8 članova. Preveliki timovi nisu praktični;
- rotacija uloga u timu svakih 3-10 minuta. Mi ćemo kotistiti **4 minute**.
  - koliko vremena za puni krug? - idealno 20-30 minuta
  - kraće vrijeme održava fokus članova tima
  - što je tim iskusniji to se može pridužiti vrijeme
- na kraju sjednice provodi se retrospektiva
- cilj:
  - **svi moraju ili učiti ili doprinositi zadatku**
- udaljeni rad:
  - podijeliti IDE
  - svi imaju upaljenu kameru - lakša komunikacija
  - koristi se neki alat za *git handover* kao što je **mob**
  - svi bi trebali imati slušalice ili jako dobre mikrofone kako ne bi došlo do mikrofonije
  - poželjno je imati uvijek uključen mikrofon (pod uvjetom da imate tihu okolinu) da se lakše možete uključiti u razgovor
    - ako to nije moguće potrebno je isključivati mikrofon dok ne pričate - potrebna praksa dok se ne naučite

### Uloge

- **vozač** (*driver/typer*):
  - sluša navigatora što mu priča i to provodi u djelo (tipka i koristi IDE)
  - ako nešto ne zna napraviti pita navigatora da mu objasni i da ga vodi u tome
  - ne tipka ništa što mu navigator nije rekao
  - nema raspravlja o problemu i rješenju
  - može se zamisliti da je pametna tipkovnica
  - ono što radi svi moraju vidjeti (dijeljenje ekrana)
- **navigator** (*navigator/talking*):
  - donosi odluke
  - vodi tim
  - nalazi rješenja
  - razgovara s članovima
  - komunicira o ciljevima - što želi postići
  - objašnjava razloge
  - traži pomoć
  - sluša članove
  - daje instrukcije vozaču tj. govori mu što da radi
    - kako govori?
      1. reći namjere - na visokoj razini
      2. lokacija - gdje treba nešto napraviti (datoteka/klasa i red)
      3. detalji - npr. pritisni ovu kombinaciju tipki, napiši ovo, klikni ovdje
- **član tima** (*mobber*):
  - razmišlja o problemu i rješenju
  - raspravlja s ostalima
  - predlaže rješenja
  - smišlja slučajeve i zapisuje na papir te kada se jedan dio završi onda se to stavi na zajedničko mjesto (zajednička ploča ili datoteka za TODO)
  - ne pita navigatora pitanja i ne nudi rješenje ako navigator nije pitao
- **sljedeći navigator** (*next navigator*)
  - nakon rotacije je ta osoba navigator
  - u ovoj rotaciji je samo član tima

  Zamjena uloga je na sljedeći način:
  
  - vozač postaje član tima
  - navigator postaje vozač
  - sljedeći član postaje navigator

  Kod udaljenog rada treba definirati redoslijed i na početku svake rotacije reći na glas svako za sebe:
  - tko (ime) je vozač
  - tko (ime) je navigator
  - tko (ime) je sljedeći navigator

### Okolina u kojoj radimo

- zajednički repozitorij na gitu (npr. GitHub)
  - svi članovi tima mogu pistati u njega (treba podesiti dozvole)
- alarm za vrijeme
  - koristiti neki alat na webu ili
  - instalirati neki alat na računalu npr. pokrenuti `mob start 4` - pokreće timer u terminalu (svakako prije provjeriti da li se čuje zvuk kada završi)
  - pokrenuti timer na telefonu
- kada se mijenjaju uloge:
  - postojeći vozač:
    - pokrene `mob next`
    - prestane dijeliti ekran
  - novi vozač:
    - pokrene dijeljenje ekrana
    - pokrene `mob start`
    - kaže da je vozač npr. Mario je vozač
    - pokrene alarm (*timer*) - na nekom alatu ili na mobitelu
  - ostale uloge kažu svoje uloge:
    - npr. Sanja je navigator. Pero je sljedeći navigator.
- kada radimo u grupama onda će se svatko priključiti kanalu na Teamsu za tu grupu
- TODO.txt - datoteka u koju pišemo slučajeve koje trebamo provjeriti da rade (ideje, informacije za testove)
- popis svih članova tima u nekom redoslijedu se stavi u kanal
  - na početku je po redu vozač, navigator, sljedeći navigator

### Kako govoriti?

- dobronamjerno
- obzirno - s puno slušanja
- s poštovanjem

Potrebno je prvo naučiti komunicirati. Za to treba prakse. Teško je kada ste u ulozi vozača ne iznositi svoje mišljenje. Na to se moramo naviknuti.

Ako postoji nekoliko ideja kako nešto riješiti onda prvo napraviti jedno rješenje pa probati drugo i onda odlučiti. Odlučiti možemo glasanjem.

Kada neko postaje navigator ima pravo odlučivanja, ali ako se ne slaže s pristupom kako se krenulo rješavati prvo treba završiti taj pristup (princip *yes, and*) pa onda probati svoje rješenje (ako stigne u svojoj navigaciji). Ako ne stigne uvijek može kao član predložiti svoje rješenje koje se može implementirati pa vidjeti što je bolje.

Nije bitno tko je rekao što ili čija je ideja, nego da se posao napravi.

### Iskustva

Brzina će doći s vremenom, obično oko 16 sat zajedničkog rada.

Uhodavanje tima oko različitih stvari traje oko 180 sati (2 mjeseca) rada. Nakon toga postaju vrlo produktivni.

## Literatura

Stranice:

- https://www.remotemobprogramming.org
- https://mobprogramming.org
- https://mobretreat.org
- https://github.com/isidore/Talks/blob/master/Mob_Programming.md

Knjiga:

- [Ensemble Programming Guidebook by Maaret Pyhäjärvi](https://mobprogrammingguidebook.xyz)
- [Remote Mob Programming by Dr. Simon Harrer, Martin Huber, and Jochen Christ](https://leanpub.com/remotemobprogramming)

Video materijali:

- [Mob Programming infoq talk](https://www.infoq.com/presentations/mob-programming/) - predavanje s kratkom sjednicom
- [Remote Mob-Programming Session facilitated by Llewellyn Falco - YouTube](https://www.youtube.com/watch?v=43DNMcwR3bk) - primjer jedne sjednice (preko 3 sata)
- [Mob-Programming Facilitation Tips & Tricks by Llewellyn Falco - YouTube](https://www.youtube.com/watch?v=ZYeM_lYJc7w) - analiza prethodne sjednice (3 sata)

Blogovi:

- [The way things work in Llewellyn's world: Llewellyn’s strong-style pairing](http://llewellynfalco.blogspot.com/2014/06/llewellyns-strong-style-pairing.html)
- [How to deliver a remote training with code-katas and randori in pairs | Philippe Bourgau’s XP Blog](http://philippe.bourgau.net/how-to-deliver-a-remote-training-with-code-katas-and-randori-in-pairs/)
- [Mob Testing: An Introduction & Experience Report](https://www.ministryoftesting.com/dojo/lessons/mob-testing-an-introduction-experience-report)
- [Our Team's First Mobbing Session](https://www.lisihocke.com/2017/04/our-teams-first-mobbing-session.html)
