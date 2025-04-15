sequenceDiagram
    participant Navegador
    participant Servidor

    %% El usuario escribe el contenido de la nueva nota en la interfaz de la SPA
    Note over Navegador: El usuario ingresa el contenido de la nota

    %% Al hacer clic en el botón "Save", se dispara un evento en el navegador
    Navegador->>Navegador: Evento "Click Save"
    Note right of Navegador: JavaScript intercepta el clic y prepara los datos en formato JSON

    %% La aplicación envía una petición POST al servidor para crear la nueva nota
    Navegador->>Servidor: POST /exampleapp/notes<br/>(payload: {"content": "Mi nueva nota"})
    activate Servidor
    Servidor-->>Navegador: Respuesta confirmando la creación de la nota<br/>(nota creada correctamente)
    deactivate Servidor

    %% El navegador actualiza la interfaz dinámicamente sin recargar la página
    Note right of Navegador: El navegador actualiza la lista de notas mostrando la nueva nota

