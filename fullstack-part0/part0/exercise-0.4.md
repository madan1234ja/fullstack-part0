sequenceDiagram
    participant browser
    participant server

    browser->>server: GET /notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET /main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET /main.js
    activate server
    server-->>browser: JavaScript file
    deactivate server

    Note right of browser: Browser starts executing JavaScript code

    browser->>server: GET /data.json
    activate server
    server-->>browser: [{ "content": "note1", "date": "..." }, ...]
    deactivate server

    Note right of browser: User types new note and clicks "Save"

    browser->>server: POST /new_note (form data)
    activate server
    server-->>browser: 302 redirect to /notes
    deactivate server

    browser->>server: GET /notes
    activate server
    server-->>browser: Updated HTML document
    deactivate server

    browser->>server: GET /main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET /main.js
    activate server
    server-->>browser: JavaScript file
    deactivate server

    browser->>server: GET /data.json
    activate server
    server-->>browser: Updated notes data
    deactivate server
