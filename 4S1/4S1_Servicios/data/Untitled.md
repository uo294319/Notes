


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
## Simple Mail Transfer Protocol
- **Def**
	- Sobre TCP.
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
    
    alt Opciones básica (1) y con má
	    MUA->>MTA: (Opción 1) HELO cliente.ejemplo.com
	    MUA->>MTA: (Opción 2) EHLO cliente.ejemplo.com
	end
	
    MTA->>MUA: 250 - OK
    MTA->>MUA: 250 - STARTTLS
    MTA->>MUA: 250 - AUTH LOGIN PLAIN
    MTA->>MUA: 250 OK

    alt Se usa cifrado
        MUA->>MTA: STARTTLS
        MTA->>MUA: 220 Ready to start TLS
        note right of MUA: TLS handshake (capa cifrada)
        activate MUA
        deactivate MUA
        MUA->>MTA: EHLO cliente.ejemplo.com
        MTA->>MUA: 250 OK
    end

    alt Si se requiere autenticación
        MUA->>MTA: AUTH LOGIN
        MTA->>MUA: 334 VXNlcm5hbWU6   (base64 challenge)
        MUA->>MTA: <usuario_base64>
        MTA->>MUA: 334 UGFzc3dvcmQ6   (base64 challenge)
        MUA->>MTA: <pass_base64>
        MTA->>MUA: 235 Authentication successful
    end

    MUA->>MTA: MAIL FROM:<remitente@ejemplo.com>
    MTA->>MUA: 250 OK
    MUA->>MTA: RCPT TO:<destino@ejemplo.org>
    MTA->>MUA: 250 OK
    MUA->>MTA: DATA
    MTA->>MUA: 354 End data with <CR><LF>.<CR><LF>
    MUA->>MTA: (Encabezados + cuerpo del mensaje)
    MUA->>MTA: .
    MTA->>MUA: 250 Message accepted for delivery
    MUA->>MTA: QUIT
    MTA->>MUA: 221 Bye
    note over MTA: El MTA entrega el mensaje a destino (lookup MX, entrega a otro MTA, etc.)
```
