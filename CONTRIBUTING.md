# Bidra til forbedringer og sånn!

Alle i organisasjonen `navikt` skal ha tilgang til å pushe til en branch, så du trenger ikke forke.

For å gjøre endringer er det sannsynligvis enklest å jobbe utenfor submodul, så klon heller repoet hvor enn du vanligvis kloner repo.

```bash
git clone git@github.com:navikt/quarto-tweaks.git
cd quarto-tweaks
# ... gjør endringene dine her
git branch min-endring
git add .
git commit -m "jeg gjorde noen kule endringer!"
git push -u origin min-endring
```