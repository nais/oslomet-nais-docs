Dette er en repo for en gruppe OsloMet-studenter som skriver bachelor-oppgave om UU.

- Kildekode som var relevant under dette prosjektet befinner seg under `cinder` katalog.

- Utplassert løsningen finnes under denne lenken: https://nais.io/oslomet-nais-docs/

### Kjøre løsningen lokalt:

Denne løsningen er mulig å kjøre lokalt ved hjelp av MkDocs programmet.
For å kunne kjøre løsningen, MkDocs samt avhengigheter er nødvendig.

- Installasjon og bruk av MkDocs:
  https://www.mkdocs.org/getting-started/

- Avhengigheter,
  disse kan installeres ved hjelp av pip:

  ```
  pip install Pygments
  pip install pymdown-extensions
  ```

  mer informasjon om dem finnes inn i `requirements.txt` fil

Etter at MkDocs og avhengigheter er på plass kan løsningen kjøres lokal.
Dette gjøres via en MkDocs kommando fra prosjektens root (katalog hvor "mkdocs.yml" befinner seg)

Kommando for å kjøre løsningen:
  ```
  MkDocs serve
  ```