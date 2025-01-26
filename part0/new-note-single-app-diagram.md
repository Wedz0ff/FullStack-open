:::mermaid

sequenceDiagram

    participant client-side
    participant server-side

    client-side->>server-side: Fill the notes_form input text and press "Save".
    Note right of client-side: The captured value from the input will be send using POST to the server.

    client-side->>server-side: HTTP POST request is sent to https://studies.cs.helsinki.fi/exampleapp/new_note_spa containing the captured input value.

    activate server-side
    server-side-->>client-side: Server sends the HTTP response status 201.
    Note right of server-side: Server receives this request to create a new note and creates it.
    deactivate server-side

    Note right of client-side: At the same time the new note will be displayed on HTML dinamically, because of how it works using spa.js

:::