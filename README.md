# Git for VG1: kom i gang uten stress

Git hjelper deg å lagre versjoner av kodeprosjektet ditt. Du kan se hva som er endret, gå tilbake til en eldre versjon og sende arbeidet til GitHub.

> **Kort forklart:** Git er programmet på PC-en din. GitHub er nettsiden der prosjektet kan ligge som en kopi og deles med andre.

## Slik tenker Git

Når du jobber med filer, går de vanligvis gjennom tre steg:

1. **Endret** – du har skrevet eller endret noe i filen.
2. **Klar til lagring** – du velger hvilke endringer som skal bli med i neste lagring.
3. **Lagret i Git** – du lager en **commit**, altså et lagringspunkt i prosjektets historie.

~~~text
Endre filer  →  git add  →  git commit
~~~

En commit er som et bilde av prosjektet akkurat da. Du kan derfor se tilbake på gamle versjoner senere.

---

## Før du starter

Du trenger:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Git](https://git-scm.com/)
- en konto på [GitHub](https://github.com/)

Åpne terminalen i VS Code med **Terminal → New Terminal**.

Sjekk først at Git virker:

~~~bash
git --version
~~~

Hvis du får et versjonsnummer, er Git installert.

### Første gang: velg navn og e-post

Git legger navnet ditt på commitene. Dette trenger du vanligvis bare å gjøre én gang på PC-en:

~~~bash
git config --global user.name "Ditt navn"
git config --global user.email "din.epost@example.com"
~~~

Bruk gjerne samme e-post som på GitHub.

---

## Start et prosjekt

Det finnes to vanlige måter å starte på.

### A. Du har allerede en prosjektmappe

Åpne mappen i VS Code, åpne terminalen og skriv:

~~~bash
git init
~~~

Git lager nå en skjult mappe som heter `.git`. **Ikke slett den**, fordi den inneholder prosjektets historikk.

### B. Prosjektet finnes allerede på GitHub

Kopier adressen til prosjektet fra GitHub og skriv:

~~~bash
git clone https://github.com/brukernavn/prosjektnavn.git
~~~

Git laster da ned prosjektet, også de gamle commitene.

---

## Den vanlige Git-rutinen

Bruk denne rekkefølgen hver gang du jobber med et prosjekt:

### 1. Hent siste versjon

~~~bash
git pull
~~~

Dette henter nye endringer fra GitHub. Gjør det før du begynner, spesielt hvis flere jobber med samme prosjekt.

### 2. Jobb med filene

Endre eller lag nye filer i VS Code. Husk å lagre filene med **Ctrl + S**.

### 3. Se hva som er endret

~~~bash
git status
~~~

Denne kommandoen er den viktigste å lære. Den viser hvilke filer Git ser, og om noe er klart til commit.

Vil du se nøyaktig hva som er endret, kan du bruke:

~~~bash
git diff
~~~

### 4. Velg det som skal lagres

For én fil:

~~~bash
git add main.py
~~~

For alle endringer i prosjektmappen:

~~~bash
git add .
~~~

Etterpå kan du skrive `git status` igjen. Da ser du hvilke filer som blir med i neste commit.

### 5. Lag en commit

~~~bash
git commit -m "La til spørsmål om navn"
~~~

Skriv kort og tydelig hva du gjorde. Dårlige meldinger er for eksempel `endring` eller `oppdatert`. Bedre meldinger er:

~~~text
La til innlogging
Rettet feil i kalkulatoren
Oppdaterte README
~~~

### 6. Send arbeidet til GitHub

~~~bash
git push
~~~

Nå er commit-en både på PC-en din og på GitHub.

---

## Koble et nytt prosjekt til GitHub

Har du brukt `git init` i en lokal mappe? Da må du gjøre dette én gang:

1. Gå til GitHub og trykk **New repository**.
2. Velg et enkelt navn, for eksempel `python-oppgaver`.
3. Velg **Private** hvis bare du og læreren skal se prosjektet.
4. Trykk **Create repository**.
5. Kopier adressen som slutter på `.git`.

Skriv deretter i terminalen:

~~~bash
git branch -M main
git remote add origin https://github.com/brukernavn/prosjektnavn.git
git push -u origin main
~~~

Bytt ut adressen med din egen. Etter dette holder det vanligvis å bruke `git pull` og `git push`.

> Ikke lag README på GitHub når du allerede har startet prosjektet lokalt. Da slipper du en unødvendig konflikt i begynnelsen.

---

## Nyttige og ofte brukte kommandoer

| Kommando | Hva den gjør |
| --- | --- |
| `git --version` | Sjekker at Git er installert. |
| `git init` | Starter Git i den åpne prosjektmappen. |
| `git clone <adresse>` | Laster ned et prosjekt fra GitHub. |
| `git status` | Viser hva som er endret og klart til commit. |
| `git diff` | Viser nøyaktig hva som er endret. |
| `git add <fil>` | Gjør én fil klar til commit. |
| `git add .` | Gjør alle endringer klare til commit. |
| `git commit -m "melding"` | Lager et lagringspunkt. |
| `git log --oneline` | Viser gamle commiter, én per linje. |
| `git pull` | Henter endringer fra GitHub. |
| `git push` | Sender commitene dine til GitHub. |

---

## Se gamle versjoner

Bruk denne kommandoen for å se historikken:

~~~bash
git log --oneline
~~~

Du får en kort liste med commit-ID og melding. Hvis du vurderer å gå tilbake til en gammel versjon i et skoleprosjekt, spør læreren først.

---

## Ikke legg dette på GitHub

Ikke legg passord, API-nøkler eller personopplysninger i prosjektet. Bruk en fil som heter `.gitignore` for å fortelle Git hvilke filer den skal hoppe over.

Eksempel:

~~~gitignore
.env
__pycache__/
venv/
node_modules/
~~~

Har du allerede sendt et passord til GitHub? Bytt passordet eller nøkkelen med en gang.

---

## Vanlige problemer

### «Jeg ser ikke endringene mine»

Skriv:

~~~bash
git status
~~~

Sjekk også at du har åpnet riktig mappe i VS Code.

### «git push blir avvist»

Noen kan ha sendt nye endringer til GitHub først. Prøv:

~~~bash
git pull
git push
~~~

### «Jeg glemte git add»

Det går helt fint. Skriv `git add .`, og lag så en ny commit.

### «Jeg fikk med en fil som ikke skal være med»

Hvis du ikke har laget commit ennå:

~~~bash
git restore --staged filnavn
~~~

Filen blir fortsatt liggende på PC-en, men tas ut av neste commit.

---

## Huskeregel

~~~bash
git pull
git status
git add .
git commit -m "Forklar endringen"
git push
~~~

**Hent → jobb → sjekk → lagre → send.**

