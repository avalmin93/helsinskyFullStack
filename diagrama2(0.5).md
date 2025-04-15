sequenceDiagram
    participant Navegador
    participant Servidor

    %% El usuario ingresa a la URL de la SPA
    Navegador->>Servidor: GET /exampleapp/spa
    activate Servidor
    Servidor-->>Navegador: HTML de la SPA
    deactivate Servidor

    %% El navegador solicita los recursos estáticos necesarios
    Navegador->>Servidor: GET /exampleapp/main.css
    activate Servidor
    Servidor-->>Navegador: Archivo CSS
    deactivate Servidor

    Navegador->>Servidor: GET /exampleapp/spa.js
    activate Servidor
    Servidor-->>Navegador: Archivo JavaScript
    deactivate Servidor

    %% El navegador ejecuta el JavaScript y solicita los datos
    Note right of Navegador: El navegador ejecuta spa.js y solicita las notas en formato JSON

    Navegador->>Servidor: GET /exampleapp/data.json
    activate Servidor
    Servidor-->>Navegador: Datos JSON de las notas
    deactivate Servidor

    Note right of Navegador: El navegador renderiza las notas utilizando JavaScript sin recargar la página
