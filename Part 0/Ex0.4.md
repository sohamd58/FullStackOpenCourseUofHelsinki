'''mermaid
sequenceDiagram
    participant user
    participant browser
    participant server

    user->>browser: Writes a note and clicks "Save"
    
    Note right of browser: The browser captures the input and prepares a POST request

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note (with note data)
    activate server
    server-->>browser: 302 Redirect to /notes
    deactivate server

    Note right of browser: The browser reloads the notes page to reflect the new note

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JavaScript file
    deactivate server

    Note right of browser: The browser executes JavaScript to fetch updated notes

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Updated JSON with new note included
    deactivate server

    Note right of browser: The browser updates the UI to display the new note
