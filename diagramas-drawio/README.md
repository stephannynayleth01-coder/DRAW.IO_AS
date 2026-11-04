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

## EJERCICIO 2A: Generalización de actores
El RPG Manager tendrá un Jugador Premium que puede hacer todo lo del Jugador y además Comprar ítem exclusivo. 
Agrega el actor Jugador Premium y conéctalo a Jugador con una generalización. 
Agrega el caso de uso CU-13 Comprar ítem exclusivo asociado solo al Jugador Premium. 
## ¿Hacia dónde apunta el triángulo vacío y por qué?
Apunta hacia el actor general (Jugador). En UML, la flecha de generalización (flecha con punta de triángulo no rellenado) siempre apunta desde el elemento especializado (Jugador Premium) hacia el elemento superclase o general (Jugador) para indicar que el primero hereda la estructura y comportamientos del segundo. 
## ¿Por qué el Jugador Premium NO necesita líneas a CU-01 … CU-10?
Porque hereda automáticamente todas las asociaciones de su actor padre (Jugador). En UML, un actor especializado dispone de todos los casos de uso con los que se relaciona el actor general del cual deriva, por lo que solo es necesario trazarle líneas hacia sus casos de uso exclusivos (en este caso, a CU-13 Comprar ítem exclusivo).

## BUG A CORREGIR 
Este diagrama tiene cuatro errores. Identifícalos: 
- Hay un caso de uso llamado "Inventario". 
- El actor Game Master está dibujado DENTRO del rectángulo del sistema. 
- La flecha «include» va de CU-04 Elegir clase hacia CU-03 Crear Personaje. 
- Hay una asociación directa entre el actor Jugador y el actor Game Master. 

Error 1: "Inventario" es un sustantivo, no un caso de uso. Un caso de uso debe representar una meta funcional expresada como verbo + sustantivo.

Error 2: El actor Game Master está dibujado dentro del límite del sistema. Los actores representan entidades o roles externos que interactúan con el sistema, por lo que conceptual y gráficamente deben ubicarse fuera del rectángulo del límite del sistema.

Error 3: _La relación «include» está invertida. La flecha punteada de «include» debe salir siempre desde el caso de uso base (CU-03 Crear Personaje) hacia el caso de uso incluido (CU-04 Elegir clase).

Error 4: Existe una asociación directa entre dos actores (Jugador y Game Master). En un diagrama de casos de uso UML no se permite conectar dos actores directamente mediante una línea de asociación; la interacción entre actores externos siempre debe realizarse indirectamente a través del sistema mediante un caso de uso.

## EJERCICIO 3A: ¿Y si se acaban las pociones? 
El paso 10 asume que el Jugador siempre tiene pociones. Agrega una decisión antes de "Restaurar vida". 
¿En qué carril va la decisión? En el carril de RPG Manager, técnicamente el sistema valida las existencias.
Guarda 1: [tiene pociones > 0]  →  ¿a qué acción va? A la acción "Restaurar vida del Personaje".
Guarda 2: [pociones == 0]  →  ¿a qué acción va? Salta la restauración y va directamente al rombo de Unión (paso 11) o muestra la acción "Informar: Sin pociones".
