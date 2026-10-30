## EJERCICIO 1A: Completa los flujos que faltan
El sistema todavía tiene dos flujos sin dibujar. Escríbelos en la tabla y agrégalos a tu diagrama: 

| # | Origen | Flujo de datos |Destino|
| --- | --------- | ------------ | ------------ |
| F10| Jugador| Credenciales de acceso (usuario y contraseña)| RPG Manager |
| F11 | Servicio de Respaldo en la Nube| Datos de la partida guardada| RPG Manager |

## BUG A CORREGIR
Un compañero entregó un diagrama de contexto con estos elementos. Encuentra los tres errores: 

- Un rectángulo "Base de datos de Personajes" conectado al círculo como entidad externa. 
- Una flecha de Jugador al círculo con la etiqueta "Crear Personaje". 
- Una flecha directa de Jugador a Game Master con la etiqueta "mensaje". 

Error 1: La Base de datos de Personajes no debe representarse como una entidad externa, porque es un componente interno del sistema y no un actor externo.

Error 2: La etiqueta «Crear Personaje» representa una acción o proceso, no un flujo de datos. Debería utilizarse «Datos del personaje» o «Solicitud de creación de personaje».

Error 3: No debe existir una conexión directa entre Jugador y Game Master, porque toda comunicación debe pasar por el sistema RPG Manager.

## Checklist del diagrama de contexto
- [x] Un solo proceso, numerado 0.
- [x] Al menos 4 entidades externas.
- [x] Todas las flechas tienen nombre de datos (sustantivo).
- [x] Ninguna flecha conecta dos entidades externas entre sí.
- [x] No hay bases de datos.

