sequenceDiagram
    participant Käyttäjä
    participant Selain
    participant Palvelin

    Note right of Käyttäjä: Käyttäjä kirjoittaa tekstin ja painaa "Tallenna"

    Selain->>Selain: Luo uusi muistiinpano (sisältö + päivämäärä)
    Selain->>Selain: Lisää muistiinpano selaimen muistissa olevaan listaan
    Selain->>Selain: Päivittää näkymän ilman sivun uudelleenlatausta

    Note right of Selain: Selain lähettää muistiinpanon palvelimelle taustalla

    Selain->>Palvelin: POST /exampleapp/new_note_spa (JSON-data)
    activate Palvelin
    Palvelin-->>Selain: Vastauksena 200 OK (jos tulee vastaus)
    deactivate Palvelin

    Note right of Selain: Selain näyttää ilmoituksen "Muistiinpano tallennettu"
