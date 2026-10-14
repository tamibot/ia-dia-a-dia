# El servidor: que corra solo

Tu laptop se apaga; un **VPS** (una computadora alquilada en la nube) no. Ahí viven:

- **n8n**: el reloj. «Todos los días a las 8:00, pide el resumen y mándalo por WhatsApp.»
- **WAHA**: tu WhatsApp conectado. Escaneas un QR, como en WhatsApp Web.

## Pasos

1. **Crea el VPS.** Ubuntu, el plan más chico. AWS Lightsail cuesta US$ 5/mes (3 meses gratis al
   empezar); Hetzner ≈ €4; DigitalOcean desde ≈ US$ 4.
2. **Pídeselo a Claude Code.** Abre esta carpeta en VS Code y escribe:
   *«Conéctate a mi VPS [IP] con la llave [archivo], instala Docker y levanta docker-compose.yml.
   Muéstrame cada paso antes de hacerlo.»*
3. **WhatsApp.** Abre `http://IP:3000/dashboard`, crea la sesión y escanea el QR con el número dedicado.
4. **n8n.** Abre `http://IP:5678`, crea tu usuario y arma el flujo:
   Horario 8:00 → leer el tablero → pedir el resumen a Claude → enviar por WAHA.

## Antes de usarlo en serio

- Pon contraseña a WAHA y a n8n y no dejes los puertos abiertos a todo internet (Claude Code te ayuda).
- Respaldo diario de la carpeta `sesiones/` y del volumen de n8n.
- Un **vigía**: si dejan de llegar mensajes, que te avise. El silencio es una alarma.
- WAHA no es la API oficial de Meta: número dedicado, nada de envíos masivos.
