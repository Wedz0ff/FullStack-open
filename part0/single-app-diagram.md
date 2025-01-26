:::mermaid

sequenceDiagram

    participant client-side
    participant server-side

    client-side->>server-side: GET https://studies.cs.helsinki.fi/exampleapp/spa
    
    client-side->>server-side: GET /main.css
    activate server-side
    server-side-->>client-side: Status 200 (main.css)
    deactivate server-side

    client-side->>server-side: GET /spa.js
    activate server-side
    server-side-->>client-side: Status 200 (main.js)
    deactivate server-side

    Note right of client-side: The client starts to execute spa.js

    client-side->>server-side: GET /data.json
    activate server-side
    server-side-->>client-side: [{"content": "Note","date": "2025-01-26T10:59:26.633Z"},{"content": "hello","date": "2025-01-26T11:08:04.453Z"},{"content": "forms","date": "2025-01-26T11:06:56.432Z" ...}]
    deactivate server-side

    Note right of client-side: The client executes the callback function that renders the notes in the SPA, this function can be found on spa.js

:::