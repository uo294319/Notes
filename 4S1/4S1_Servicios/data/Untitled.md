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
			- Grupos de `3B` (`24b`) divididos en trozos de `6b`