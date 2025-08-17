sequenceDiagram

    Note right of selain: Käyttäjä kirjoittaa muistiinpanon tekstikenttään ja painaa "Tallenna"-painiketta

    selain->>selain: Estää lomakkeen oletustoiminnon (JavaScript event.preventDefault)

    selain->>palvelin: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate palvelin
    Note right of selain: Selain lähettää lomakkeen tiedot (esim. content=Uusi+muistiinpano&date=2025-08-17)
    palvelin-->>selain: 302 Uudelleenohjaus -> /exampleapp/notes
    deactivate palvelin

    Note right of selain: Selain seuraa uudelleenohjausta ja lataa uudelleen muistiinpanosivun

    selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate palvelin
    palvelin-->>selain: HTML-dokumentti
    deactivate palvelin

    selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate palvelin
    palvelin-->>selain: CSS-tiedosto
    deactivate palvelin

    selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate palvelin
    palvelin-->>selain: JavaScript-tiedosto
    deactivate palvelin

    Note right of selain: Selain suorittaa JavaScript-koodin, joka hakee muistiinpanot JSON-muodossa

    selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate palvelin
    palvelin-->>selain: Päivitetty JSON, joka sisältää myös uuden muistiinpanon
    deactivate palvelin

    Note right of selain: Selain suorittaa palautuskutsun (callback), joka piirtää muistiinpanot näkyviin
