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
- Formato: `Campo: valor\r\n`.
- 
- Definidas en el MUA
	- `From`, `To`, `Reply-to`, `Cc`, `Bcc`, `Subject`, `Date`, `Message-Id`
- Añadidas por MTAs: 
	- Por primer MTA, si no las define MUA: `Date`, `From`, `To`, `Message-Id`
	- MTAs intermedios `Received`
	- Añadida por último MTA destino: `Return-Path`
	- Fin encabezado: `\r\n\r\n`
	- Cuerpo.
- Cabeceras: 