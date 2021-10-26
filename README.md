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
  - [Kako krenuti?](#kako-krenuti)
    - [Dohvaćanje inicijalnog projekta iz predloška](#dohvaćanje-inicijalnog-projekta-iz-predloška)
    - [Podešavanje prava pisanja](#podešavanje-prava-pisanja)
    - [Kloniranje i uvoz repozitorija u IDE](#kloniranje-i-uvoz-repozitorija-u-ide)
    - [Jedna rotacija](#jedna-rotacija)
  - [Retrospektiva](#retrospektiva)
  - [Problemi kod korištenja alata mob](#problemi-kod-korištenja-alata-mob)
    - [Nismo snimili datoteke prije prebacivanja na novog vozača](#nismo-snimili-datoteke-prije-prebacivanja-na-novog-vozača)
      - [Sljedeći vozač nije napravio još ništa](#sljedeći-vozač-nije-napravio-još-ništa)
      - [Drugi vozač je već preuzeo kod, ali nije ništa mijenjao](#drugi-vozač-je-već-preuzeo-kod-ali-nije-ništa-mijenjao)
      - [Drugi vozač je već preuzeo kod, pokrenuo sjednicu i promijenio datoteku](#drugi-vozač-je-već-preuzeo-kod-pokrenuo-sjednicu-i-promijenio-datoteku)
  - [Literatura](#literatura)

<!-- /TOC -->

## Priprema za rad

### Instalacija programa

- Java 11+ - [upute](https://www.fer.unizg.hr/_download/repository/01.1-Podesavanje_varijabli_okruzenja.pdf)
  - Windows: 
    - Oracle [JDK 17 General-Availability Release](https://jdk.java.net/17/)
    - [Eclipse Tumerin](https://adoptium.net/)
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
- *Enesemble Programming* - preporuča se jer nema negativne konotacije

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

- **vozač** (*driver/typist*):
  - sluša navigatora što mu priča i to provodi u djelo (tipka i koristi IDE)
  - ako nešto ne zna napraviti pita navigatora da mu objasni i da ga vodi u tome
  - ne tipka ništa što mu navigator nije rekao
  - ne raspravlja o problemu i rješenju
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
- **član tima** (*member/mobber*):
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
- kada radimo u *online* grupama onda će se svatko priključiti kanalu na Teamsu za tu grupu
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

Brzina će doći s vremenom, obično oko 16 sati zajedničkog rada.

Uhodavanje tima oko različitih stvari traje oko 180 sati (2 mjeseca) rada. Nakon toga postaju vrlo produktivni.

## Kako krenuti?

### Dohvaćanje inicijalnog projekta iz predloška

Upute za stvaranje repozitorija iz predloška su [ovdje](https://docs.github.com/en/free-pro-team@latest/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template).

Otići na stranicu repozitorija na GitHubu npr. [https://github.com/MarioKusek/ilj-tdd-template](https://github.com/MarioKusek/ilj-tdd-template) ili [https://github.com/MarioKusek/ilj-web-server-template](https://github.com/MarioKusek/ilj-web-server-template), kliknuti na **Use this template**, zatim upišemo za ime rpozitorija koji ćemo stvoriti npr. `ilj-web-server`. Klik na **Create repository from template**.

Ako smo promijenili ime projekta potrebno je kliknuti na datoteku `settings.gradle`, kliknuti na olovku i zamijeniti novo ime projekta npr.

```
rootProject.name = 'novo-ime-projekta'
```

Nakon toga je potrebno kliknuti na **Commit changes**.

### Podešavanje prava pisanja

Kada smo napravili repozitorij potrebno je dodati sve članove grupe (tima) koji će moći pisati po repozitoriju. Originalne upute su [ovdje](https://docs.github.com/en/free-pro-team@latest/github/setting-up-and-managing-your-github-user-account/inviting-collaborators-to-a-personal-repository).

Kliknemo na **Settings** pa na **Manage Access**. Kliknemo na gumb **Invite a colaborator**. U obrascu trebamo dodati korisnička imena ili email člana tima. Kada ga github pronađe trebamo kliknuti za dodavanje.
Korisnik će dobiti pozivnicu na email pa ju treba potvrditi.
To treba napraviti za svakog korisnika posebno. Informacije o korisniku na githubu je nabolje razmijeniti kao poruke na kanalu u MS Teamsu ako radimo *online*.

### Kloniranje i uvoz repozitorija u IDE

Potrebno je klonirati projekt. Na stranici projekta kopiramo URI projekta. Nakon toga u direktoriju u kojem ga želimo klonirati napišemo:

```sh
git clone https://github.com/mkwinilj/ilj-web-server.git
```

Nakon toga projekt možemo *importati* u IDE pomoću **Import Existing Gradle Project**.

### Jedna rotacija

Vozač treba započeti sa rotacijom tako da u terminalu (git bash) napiše:

```sh
mob start 4
```

Broj 4 je za obavještavanje kada je prošlo 4 minute (ako to radi u vašoj postavci sustava). Nakon toga pokreće *timer* ako je to potrebno.
Broj 4 se može izostaviti ako se koristi neki drugi *timer*.

Ako smo gotovi s nekom funkcionalnošću onda pokrećemo:

```sh
mob done
```

Nakon toga je potrebno napraviti:

```sh
git commmit -m "poruka"
git push
```

I nakon toga ponovno pokrećemo:

```sh
mob start
```

Kada trebamo prebaciti rotaciju onda pokrećemo:

```sh
mob next
```

## Retrospektiva

Retrospektiva služi da se prisjetimo što se dogodilo u jednoj sjednici i što bismo mogli poboljšati.
Trebamo si postaviti pitanja iz sljedećih kategorija:

- alati
  - Koje alate smo koristili?
  - Što smo naučili?
  - Koje smo imali probleme?
  - Još neki komenari?
- učenje
  - Što smo naučili?
- emocije
  - Jesam li osjetio neke emocije?
  - Što se dogodilo da sam to osjetio?
- tim
  - Kako smo radili u timu (dobre stvari, problemi)?
- problemi
  - Neki drugi problemi koji su se dogodili?

## Problemi kod korištenja alata `mob`

Ono što je bitno naglasiti je da alat `mob` prilikom pokretanja sjednice kreira granu (*branch*) pod imenom `mob-session`. U tu granu se spremaju međurezultati između različitih vozača.

Kada se pokrene `mob next` onda se trenutno promijenjene datoteke *commitaju* u tu granu i grana se prebaci na **origin/mob-session**, a lokalno se git prebaci na **master**.

Kada drugi vozač pokrene `mob start` onda se ta grana povuče sa **origina** i lokalni git se prebaci na nju.

Prilikom završavanja sjednice pokretanjem `mob done` git postojeću granu obriše, a zadnje stanje se spoji (*squash*) u granu iz koje je krenuto (obično **master**) i tada se može to stanje *commitati*.

### Nismo snimili datoteke prije prebacivanja na novog vozača

Ako nismo snimili datoteke, a pokrenuli smo `mob next` sadržaj promijenjenih datoteka ostaje u uređivaču (*editor*) i ne prenosi se na udaljeni gitov repozitorij pa drugi vozač ne može to preuzeti.

Glavni problem je ako *editor* prati promjene na disku i primijeti da je došlo do promjene te ponovno učita datoteku sa diska. U tom slučaju je ono što smo imali u *editoru* izgubljeno.

Slijede rješenja za pojedine slučajeve.

#### Sljedeći vozač nije napravio još ništa

Rješenje je sljedeći postupak:

1. ponovno pokrenemo sjednicu s `mob start`,
2. ako *editor* pita da se učita nešto sa diska to treba odbiti
3. snimiti datoteku
4. prebaciti sjednicu na sljedećeg vozača pokretenjem `mob next`

#### Novi vozač je već preuzeo kod, ali nije ništa mijenjao

Novi vozač treba napraviti:

1. ako je već napravio `mob start`onda treba prebaciti sjednicu tako da pokrene `mob next`, a ako nije onda ovaj korak treba preskočiti

Prethodni vozač:

1. ponovno pokrenemo sjednicu s `mob start`,
2. ako *editor* pita da se učita nešto sa diska to treba odbiti
3. snimiti datoteku
4. prebaciti sjednicu na sljedećeg vozača pokretenjem `mob next`

Nako toga novi vozač može pruzeti sjednicu sa `mob start`.

#### Novi vozač je već preuzeo kod, pokrenuo sjednicu i promijenio datoteku

U ovom slučaju imamo dvije mogućnosti:

1. ako ne želimo promjenu novog vozača zadržati

    a. novi vozač: vratimo originalnu verziju datoteke `git checkout ime_datoteke`

    b. novi vozač: prebacimo sjednicu `mob next`

    c. prethodni vozač: preuzme sjednicu `mob start`

    d. prethodni vozač: snimi datoteku

    e. prethodni vozač: prebaci sjednicu `mob next`

    f. novi vozač: preuzme sjednicu: `mob start`

2. ako želimo promjenu novog vozača zadržati

    a. novi vozač: snimi datoteku

    b. novi vozač: `mob next`

    c. prethodni vozač: snimi datoteku

    d. prethodni vozač: spremi ovu verziju datoteke `git stash`

    e. prethodni vozač: preuzme sjednicu `mob start`

    f. prethodni vozač: spoji datoteke `git stash pop`

    g. prethodni vozač: otvori sve datoteke koje imaju konflikte i popravi ih ručno

    h. prethodni vozač: doda sve datoteke u indeks gita `git add .`

    i. prethodni vozač: prebaci sjednicu `mob next`

    j. novi vozač: preuzme sjednicu `mob start`

## Literatura

Stranice:

- https://www.remotemobprogramming.org
- https://mobprogramming.org
- https://mobretreat.org
- https://github.com/isidore/Talks/blob/master/Mob_Programming.md
- [Samman Technical Coaching](https://www.sammancoaching.org)
- https://cyber-dojo.org

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
