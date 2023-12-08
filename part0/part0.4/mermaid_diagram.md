sequenceDiagram 
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: This is the moment when the browser starts executing the JS code. The browser get to the part where the JS code tells it to GET the data from the JSON file that contains the notes on the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "NOTES",...}...]
    deactivate server

    Note left of server: At this moment the server executes the callback function that allows the notes to be displayed on the page. 

    Note right of browser: (Before this line, the diagram represents the same informations as the one shown on part0.4 exercise of the corse, from this line going down, I will be explaining how the operations undergoing when whe upload a new note in this type of web page design)

    Note right of browser: The user writes "1234" on the form an hits save. The action of our element form is "/new_note" and the methode is "POST". The browser then tries to send the content of the form POSTing it to "/new_note" 

    browser->>server: POST Form Data (note:"1234") to /exampleapp/new_note
    activate server
    server-->>browser: 302 Redirection to https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate server

    Note left of server: What has happened is that the server has got the content and it has added it to the json file, and now is telling our browser to fetch the webpage as it was done in the begining. Efectively making our browser fetch everysingle component of the webpage again, therefore asking for the updated json file that contains our newly sent note to the server.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: This is the moment when the browser starts executing the JS code. The browser get to the part where the JS code tells it to GET the data from the JSON file that contains the notes on the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "NOTES",...}...]
    deactivate server

    Note right of browser: At this moment the browser executes the callback function that allows the notes to be displayed on the page and our note is shown. 

