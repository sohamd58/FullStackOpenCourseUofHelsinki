:::mermaid
sequenceDiagram
    participant user
    participant browser
    participant server

    user->>browser: Writes a note and clicks "Save"
    Note right of browser: The browser captures input and updates UI instantly

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa (with note data)
    activate server
    server-->>browser: JSON response with saved note
    deactivate server

    Note right of browser: The browser updates the UI dynamically without reloading
:::

