# quarto-tweaks

Noen småting til Quarto som forhåpentligvis kan hjelpe med utseende og språk.
Dette er veldig i startfasen, så ikke forvent en kjempeenkel "utvikleropplevelse".

## Installering

Man kan ta i bruk disse filene på et par vis.

### `git submodule`

Man kan integrere disse filene til ditt eget prosjekt ved hjelp av `git submodule`.
Mens du befinner deg i grunnkatalogen til prosjektet ditt:

```bash
git submodule add git@github.com:navikt/quarto-tweaks.git
```

Dette vil opprette en katalog, `quarto-tweaks/`, i prosjektet ditt, samt en `.gitmodules`-fil. 
Disse kan trygt committes.
Som submodul vil den peke til dette repoet, og med `git submodule`-kommandoer skal det være enkelt å oppdatere.

Merk at ved bruk av submodules kan det endre måten du bruker `git` på:

- Folk som kanskje jobber i ditt prosjekt må kjøre `git submodule init` for å hente submodulen som du har committa.
- `git submodule update` oppdaterer submodules
- `git pull --recurse-submodules` drar inn endringer i submodul(ene) óg (typ som `git pull && git submodule update`)
- `git clone --recurse-submodules` kloner repoet, inkludert submodul(ene) óg (typ som `git clone git@github.com:navikt/quarto-prosjektet-mitt.git && cd quarto-prosjektet-mitt && git submodule init`)

En kort artikkel om submodules finnes her: https://gist.github.com/gitaarik/8735255

### Kopier filene du ønsker til ditt eget prosjekt

Dette er kanskje enklest, men det kan gjøre det mer slitsomt å oppdatere i etterkant.
Altså, ved oppdatering må du kopiere filer inn på nytt.

## Filer

Her er en liste over filer som kan være til nytte for deg.
Eksemplene antar at du benytter dette repoet som submodul.

### `_quarto_language.yml`

Dette er en språkdefinisjon, og gjør det aller meste i Quarto til norsk.
For å ta den i bruk må du i `_quarto.yml` legge inn følgende:

```diff
  project:
    type: website
    render:
      - "*.qmd"
      - "!figurer/"

+ language: quarto-tweaks/_quarto_language.yml
```

### `custom.scss`

Denne filen utvider themet "cosmo". Det er usikkert om denne vil være til nytte dersom du bruker andre themes.
I `_quarto.yml`, legg inn følgende:

```diff
format:
  html:
    theme: 
+     - quarto-tweaks/custom.scss
      - cosmo
```

### `easychart-theme.json`

Denne filen endrer farger i grafer fra [easychart](https://easychart.readthedocs.io/en/latest/index.html).
Dette er uheldigvis den ressursen som er vanskeligst å ta i bruk.

Hvor enn du bruker easychart:

```python
chart = easychart.new("column")
# ... hva enn du måtte ønske å gjøre på `chart`

# theme må sannsynligvis endres basert på hvor .qmd-filen ligger,
# relativt til hvor easychart-theme.json ligger
easychart.render(chart, theme="../quarto-tweaks/easychart-theme.json")                         
```

### `nav-logo-red.svg`

Denne filen er en NAV-logo til bruk i navbar, tatt fra andre rapporter. :)
I `_quarto.yml`, legg inn følgende:

```diff
website:
  navbar:
+   logo: quarto-tweaks/nav-logo-red.svg  
```