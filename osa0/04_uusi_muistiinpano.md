Tehtävä 0.4: uusi muistiinpano

Kaavio, joka kuvaa, mitä tapahtuu tilanteessa, jossa käyttäjä luo uuden muistiinpanon ollessaan sivulla https://studies.cs.helsinki.fi/exampleapp/notes eli kirjoittaa tekstikenttään jotain ja painaa nappia tallenna.

```mermaid
sequenceDiagram
  participant selain
  participant palvelin

  selain->>palvelin: POST https://studies.cs.helsinki.fi/exampleapp/new_note
  palvelin->>selain: 302 (HTTP-statuskoodi), uudelleenohjauspyyntö osoitteeseen /notes
  Note right of palvelin: Palvelin luo uutta muistiinpanoa vastaavan olion ja laittaa sen muistiinpanot sisältävään taulukkoon notes
  selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/notes
  palvelin-->>selain: HTML-koodi
  selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/main.css
  palvelin-->>selain: main.css
  selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/main.js
  palvelin-->>selain: main.js
  Note left of selain: Selain pyytää palvelimelta JSON-datan.
  selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/data.json
  palvelin-->>selain: [{content: "miau", date: "2023-10-27"}, ...]
  Note left of selain: Selain suorittaa tapahtumankäsittelijän, joka renderöi muistiinpanot ruudulle


```
