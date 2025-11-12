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
- Mensaje:
	- Cabeceras: `Campo: valor\r\n`.
	- Fin encabezado: `\r\n\r\n`
	- Cuerpo.
- Cabeceras
	- From
	- To
	- Reply-to
	- CC
	- Bcc
	- Subject
	- Date
	- Mess