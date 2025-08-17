mermaid
sequenceDiagram
    participant Käyttäjä
    participant Selain
    participant Palvelin

    Note over Käyttäjä: Käyttäjä kirjoittaa muistiinpanon tekstikenttään ja painaa "Tallenna"

    Selain->>Selain: Estää lomakkeen oletustoiminnon (event.preventDefault)
    Selain->>Palvelin: POST /exampleapp/new_note
    Note right of Selain: Lähetetään lomakkeen tiedot, esim. content=Muistiinpano&date=2025-08-17
    Palvelin-->>Selain: Vastaa 302 Redirect -> /exampleapp/notes

    Note over Selain: Selain seuraa uudelleenohjausta

    Selain->>Palvelin: GET /exampleapp/notes
    Palvelin-->>Selain: HTML-sivu

    Selain->>Palvelin: GET /exampleapp/main.css
    Palvelin-->>Selain: CSS-tiedosto

    Selain->>Palvelin: GET /exampleapp/main.js
    Palvelin-->>Selain: JavaScript-tiedosto

    Note over Selain: JavaScript hakee JSON-datan palvelimelta

    Selain->>Palvelin: GET /exampleapp/data.json
    Palvelin-->>Selain: JSON, joka sisältää myös uuden muistiinpanon

    Selain->>Selain: Renderöi muistiinpanot sivulle
