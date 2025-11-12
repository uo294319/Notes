


---
# Correo

[Back to index](../README.md)

---

## Introducción
- **Elementos**
	- Remitente y Destinatario
	- Message User Agent (MUA).
		- Cliente instalado en el ordenador del usuario que permite enviar y obtener correos.
	- Message Transfer Agent (MTA)
		- MTA Relay. Actúa como punto de entrada/salida en una intranet. Funciones de proxy.
		- MTA Abierto. Permite envío sin autenticación. Usado por spammers
	- Buzón
		- Almacenado en el MTA destino.
- **Protocolos**
	- SMTP. Se usa para enviar mensajes del MUA al MTA y entre MTAs
	- POP3 e IMAP. Se usan para obtener mensajes del buzón.

---
## Mensaje
### Cabeceras
- **Formato**: Varios `Campo: valor\r\n` y terminadas por `\r\n\r\n`
- **Algunas Cabeceras**
	- Definidas en el MUA
		- `From`, `To`, `Reply-to`, `Cc`, `Bcc`, `Subject`, `Date`, `Message-Id`
	- Añadidas por MTAs: 
		- Por primer MTA, si no las define MUA: `Date`, `From`, `To`, `Message-Id`
		- MTAs intermedios `Received`
		- Añadida por último MTA destino: `Return-Path`
### Cuerpo
- **Formato**. Secuencia de líneas compuestas por caracteres ASCII de `7b`.
- **Multipurpose Internet Mail Extensions (MIME)**.
	- Permite transmitir diversos contenidos como binarios en el cuerpo.
	- Permite varias partes en mismo mensaje (adjuntos, alternativos, etc)
- **Cabeceras**.
	- `MIME-version: <versión>`.
	- `Content-Type: <type>`
		- **Básicas**: `text/plain`, `text/html`, `image/jpeg`, `video/mpeg`...
		- **Multiparte**:  (cada elemento interior tiene sus propias cabeceras)
			- `multipart/mixed`. MUA muestra multiples partes. (Adjuntos, imágenes...)
			- `multipart/alternative`. MUA muestra una de las alternativas.
			- Separación partes:
				- Define cadena arbitraria: `Content-Type: <type>; boundary="<cadena>"`
				- Antes de cada parte `--<cadena>`. Al final de la última `--<cadena>--`
	- `Content-Transfer-Encoding <encoding>`
		- `7bit`. ASCII puro.
		- `quoted-printable`.
			- Caracteres no imprimibles como `=XX` siendo `XX` su código hex.
			- Líneas limitadas a 76 caracteres. Si más largas, `=` al final de la línea cortada.
		- `base64`
			- Grupos de `3B` (`24b`) divididos en trozos de `6b`.
			- Cada trozo codificado como:
				- `0-25 = "A"-"Z"` / `26-51 = "a"-"z"`
				- `52-61 = "0" - "9"` / `62 = "+"` / `63 = "/"`
			- Si contenido no múltiplo de `3B` completar con `0`s. 
				- Si último trozo `1B` terminar con `==`, si `2B` con `=`
---
## Simple Mail Transfer Protocol (SMTP)
- **Def**
	- Sobre TCP 25.
	- Puede ir autenticado (entre MUA y MTA) y opcionalmente cifrado (TLS)
- **Funcionamiento**. Usa `\r\n`como terminador.
	- Petición: `<comando> <parámetros>
	- Respuesta: `<código> <descripción>`
```mermaid
sequenceDiagram
    participant MUA as MUA (Cliente)
    participant MTA as MTA (Servidor SMTP)

    note over MUA,MTA: Conexión TCP al puerto 25
    MTA->>MUA: 220 smtp.server.com service ready
    
    alt Opciones Funcionalidad
	    MUA->>MTA: (Opción 1) HELO cliente.ejemplo.com
	    MUA->>MTA: (Opción 2) EHLO cliente.ejemplo.com
	    MTA->>MUA: 250 - OK
	end
	
	alt Cifrado (EHLO)
		MUA->>MTA: STARTTLS
		MTA->>MUA: 220 - Ready to start TLS
	end
	
	alt Autenticación (EHLO)
		MUA->>MTA: AUTH <LOGIN / PLAIN / OAuth2>
		MTA->>MUA: ?
	end
	
    MUA->>MTA: MAIL FROM: <remitente@dominio1>
    MTA->>MUA: 250 - OK
    
    MUA->>MTA: RCPT TO: <destino1@dominio2>
    MTA->>MUA: 250 - OK

	MUA->>MTA: RCPT TO: <destino2@dominio3>
    MTA->>MUA: 250 - OK
    
    MUA->>MTA: DATA
    MTA->>MUA: 354 - Start mail input
    MUA->>MTA: Línea 1
    MUA->>MTA: Línea 2
    MUA->>MTA: .
    MTA->>MUA: 250 - OK
    
    MUA->>MTA: QUIT
    MTA->>MUA: 221 smtp.server.com closing transmission chanel
```
---
## Post Office Protocol (POP3)
- **Def**
	- Sobre TCP 110
	- Permite consultar número de mensajes, descargar y borrar.
	- Su finalidad es transferir los mensajes al MUA y borrarlos en el MTA.
- **Estados**
	- **Autorización**
		- (Opción 1) Contraseña. Comandos `USER` y `PASS`
		- (Opción 2)
			- Servidor manda timestamp
			- Usuario manda 
	- **Transacción**
		- `STAT`. Número de mensajes en buzón y total bytes buzón.
		- `LIST [m]`. Cuantos bytes ocupa mensaje `m` o cada mensaje del buzón.
		- `RETR m`. Descarga mensaje `m`.
		- `DELE m`. Marca para borrado `m`.
		- `TOP m n`.  Descarga primeras `n` líneas de mensaje `m`
		- `QUIT`. Desconexión y borrado de mensajes marcados.
	- **Actualización**
		- Ocurre cuando el cliente manda `QUIT`. 
		- Se borran los mensajes marcados.
---
## Internet Message Access Protocol (IMAP)
- Def
	- Mensajes originales se mantienen en el servidor. 
	- Varios MUA pueden acceder a mensajes obteniendo copias consideradas caché.
	- Se pueden clasificar mensajes en carpetas del servidor y realizar búsquedas.
- Funcionamiento. Etiquetas arbitrar
	- Comandos MUA: `<etiqueta> <comando> <parámetros>`
	- Respuestas MTA:
		- Datos o respuestas parciales sin etiquetar
		- Resultado final etiquetado `<etiqueta> <`
- 