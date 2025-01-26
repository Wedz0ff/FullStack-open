:::mermaid

sequenceDiagram

    participant client-side
    participant server-side

    client-side->>server-side: Fill the new_note input and press "Save".
    Note right of client-side: The captured value from the input will be send using POST to the server.

    client-side->>server-side: HTTP POST request is sent to /new_note containing the captured input value.

    activate server-side
    Note right of server-side: Server receives this request to create a new note and creates it.
    server-side-->>client-side: Server sends the HTTP 302 redirect to /notes
    deactivate server-side

    Note right of client-side: Client-side receives this HTTP status and redirect to /notes

    client-side->>server-side: GET /notes
    activate server-side
    server-side-->>client-side: HTML document
    deactivate server-side

    client-side->>server-side: GET /main.css
    activate server-side
    server-side-->>client-side: the css file
    deactivate server-side

    client-side->>server-side: GET /main.js
    activate server-side
    server-side-->>client-side: the JavaScript file
    deactivate server-side

    Note right of client-side: The client-side starts executing the JavaScript code that fetches the JSON from the server

    client-side->>server-side: GET /data.json
    activate server-side
    server-side-->>client-side: [{"content": "Note","date": "2025-01-26T10:59:26.633Z"},{"content": "hello","date": "2025-01-26T11:08:04.453Z"},{"content": "forms","date": "2025-01-26T11:06:56.432Z" ...}]
    deactivate server-side

    Note right of client-side: The client-side executes the callback function that renders the notes

:::