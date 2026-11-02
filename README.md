# Brukerveiledning: Git

> For VG1-elever · Lage og lagre versjoner av kodeprosjekter

Git er et verktøy som lagrer historikken til prosjektet ditt. Du kan se hva som er endret, gå tilbake til en eldre versjon og samarbeide med andre uten å sende mange kopier av samme mappe.

## Dette lærer du

- opprette et Git-prosjekt i Visual Studio Code
- lagre endringer som en commit
- sende prosjektet til GitHub og hente det på en annen PC
- unngå å dele passord og andre hemmelige filer

## Før du begynner

Du trenger:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Git](https://git-scm.com/)
- en konto på [GitHub](https://github.com/)

Installer Git fra git-scm.com. Etterpå kan du åpne en ny terminal i VS Code med **Terminal → New Terminal**.

---

## Del 1: Start et Git-prosjekt

### 1. Start Git i prosjektmappen

Åpne prosjektmappen i VS Code. Åpne terminalen nederst og skriv:

~~~bash
git init
~~~

Git lager nå en skjult mappe som heter `.git`. **Ikke slett den.** Den inneholder prosjektets historikk.

### 2. Se hvilke filer Git har oppdaget

~~~bash
git status
~~~

Nye eller endrede filer vises ofte i rødt. Det betyr ikke at noe er galt — Git forteller bare at de ikke er lagt til i neste commit ennå.

### 3. Legg filer klare og lag en commit

~~~bash
git add .
git commit -m "Lagde første versjon av prosjektet"
~~~

Punktumet i `git add .` betyr **alle filer i denne mappen**. En god commit-melding forklarer kort hva du har gjort.

### 4. Sjekk resultatet

~~~bash
git log --oneline
~~~

Du skal nå se commit-en din med et kort ID-nummer og meldingen du skrev.

---

## Del 2: Koble prosjektet til GitHub

Git fungerer på PC-en din. GitHub er en nettside der du kan ha en sikker kopi og samarbeide med andre.

### 1. Lag et repository på GitHub

1. Logg inn på [github.com](https://github.com/) og trykk **New repository**.
2. Gi prosjektet et enkelt navn, for eksempel `python-oppgaver`.
3. Velg **Private** hvis bare du og læreren skal se prosjektet, eller **Public** hvis alle kan se det.
4. Trykk **Create repository**.

> Ikke velg README akkurat nå hvis du allerede har brukt `git init` lokalt.

### 2. Koble den lokale mappen til GitHub

GitHub viser en adresse som slutter på `.git`. Kopier den og bruk den i kommandoene under:

~~~bash
git branch -M main
git remote add origin https://github.com/brukernavn/prosjektnavn.git
git push -u origin main
~~~

Bytt ut `brukernavn` og `prosjektnavn` med din egen adresse. Første gang kan GitHub be deg om å logge inn i nettleseren.

## Vanlig arbeidsflyt hver gang du jobber

| Steg | Kommando | Hva den gjør |
| --- | --- | --- |
| 1. Hent | `git pull` | Henter arbeid som finnes på GitHub. |
| 2. Jobb | — | Endre eller lag nye filer i VS Code. Husk `Ctrl + S`. |
| 3. Kontroller | `git status` | Sjekk hva som er endret. |
| 4. Klargjør | `git add .` | Velg alle endringene til neste commit. |
| 5. Lagre | `git commit -m "Forklar endringen"` | Lag et lagringspunkt. |
| 6. Send | `git push` | Send commit-en til GitHub. |

---

## Del 3: Eksempel med en Python-oppgave

Du har laget `main.py` med et program som spør om brukerens navn. Etter at programmet virker, gjør du dette i terminalen:

~~~bash
git status
git add main.py
git commit -m "La til spørsmål om navn"
git push
~~~

Senere finner du en feil. Rett feilen, test programmet og kjør de samme kommandoene igjen. GitHub vil da vise to lagringspunkter i stedet for at den gamle versjonen blir borte.

---

## Bruke Source Control i VS Code

Du kan også bruke Git uten å skrive alle kommandoene. Trykk på **Source Control**-ikonet i menyen til venstre i VS Code.

- Trykk **+** ved en fil for å gjøre det samme som `git add`.
- Skriv en kort melding øverst og trykk **Commit**.
- Trykk **Sync Changes** eller **Publish Branch** for å sende til GitHub.

Terminalkommandoene er likevel nyttige når noe ikke virker.

---

## Viktig sikkerhet

Ikke legg passord, API-nøkler eller personopplysninger på GitHub. Selv et privat repository kan deles ved en feil. Bruk en fil som heter `.gitignore` for filer Git skal overse.

Eksempel på innhold i `.gitignore`:

~~~gitignore
.env
__pycache__/
venv/
~~~

Hvis du allerede har sendt et passord til GitHub, må du endre passordet eller nøkkelen med en gang.

---

## Vanlige problemer

| Problem | Hva du kan gjøre |
| --- | --- |
| Jeg ser ikke endringene | Skriv `git status`. Sjekk at du åpnet riktig mappe i VS Code. |
| `git push` blir avvist | Kjør `git pull` først. GitHub kan ha endringer du mangler. |
| Jeg glemte `git add` | Kjør `git add .` og lag en ny commit. Ingenting er ødelagt. |
| Jeg vil se eldre versjoner | Bruk `git log --oneline`. Spør læreren før du går tilbake til en gammel versjon. |

---

## Kort oppsummering

Git hjelper deg å holde orden på arbeidet ditt. Den viktigste rekkefølgen er:

~~~bash
git pull
git status
git add .
git commit -m "Forklar endringen"
git push
~~~

Husk: **Hent → jobb → kontroller → lagre → send.**

