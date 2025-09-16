sequenceDiagram
    participant browser
    participant server

    Note right of browser: User types new note and clicks "Save"

    browser->>browser: JavaScript captures form submission
    browser->>server: POST /new_note_spa (JSON data)
    activate server
    server-->>browser: 201 Created
    deactivate server

    Note right of browser: Browser updates the notes list dynamically without reload
