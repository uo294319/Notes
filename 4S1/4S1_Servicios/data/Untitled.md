---

---



---
- Remitente y Destinatario
- Message User Agent (MUA)
- Message Transfer Agent (MTA)
	- MTA Relay. Actúa como punto de entrada/salida en una intranet. Funciones de proxy.
	- MTA Abierto. Permite envío sin autenticación. Usado por spammers
- Buzón
	- Almacenado en el MTA destino.
---
SMTP
POP3 o IMAP

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
### Cuerpo (MIME)
- **Def (MIME)**.
	- Permite transmitir diversos contenidos como binarios en el cuerpo.
	- Permite varias partes en mismo mensaje (adjuntos, alternativos, etc)
- **Formato**. Secuencia de líneas compuestas por caracteres ASCII de `7b`.
- **Cabeceras**.
	- `MIME-version: <versión>`.
	- `Content-Type: <type>`
		- **Básicas**: `text/plain`, `text/html`, `image/jpeg`, `video/mpeg`...
		- **Multiparte**:  (cada elemento interior tiene sus propias cabeceras)
			- `multipart/mixed`. Multiples partes se . (Adjuntos, imágenes...)
			- `multipart/alternative`. Varias alternativas. Se muestra una al destinatario.
	- `Content-Transfer-Encoding <encoding>`
		- `7bit`. ASCII puro.
		- `quoted-printable`. 
		- `base64`