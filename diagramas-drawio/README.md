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

# Error 1: 
La Base de datos de Personajes no debe representarse como una entidad externa, porque es un componente interno del sistema y no un actor externo.
# Error 2: 
La etiqueta «Crear Personaje» representa una acción o proceso, no un flujo de datos. Debería utilizarse «Datos del personaje» o «Solicitud de creación de personaje».
# Error 3: 
No debe existir una conexión directa entre Jugador y Game Master, porque toda comunicación debe pasar por el sistema RPG Manager.

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

# Error 1: 
"Inventario" es un sustantivo, no un caso de uso. Un caso de uso debe representar una meta funcional expresada como verbo + sustantivo.
# Error 2: 
El actor Game Master está dibujado dentro del límite del sistema. Los actores representan entidades o roles externos que interactúan con el sistema, por lo que conceptual y gráficamente deben ubicarse fuera del rectángulo del límite del sistema.
# Error 3: 
La relación «include» está invertida. La flecha punteada de «include» debe salir siempre desde el caso de uso base (CU-03 Crear Personaje) hacia el caso de uso incluido (CU-04 Elegir clase).
# Error 4: 
Existe una asociación directa entre dos actores (Jugador y Game Master). En un diagrama de casos de uso UML no se permite conectar dos actores directamente mediante una línea de asociación; la interacción entre actores externos siempre debe realizarse indirectamente a través del sistema mediante un caso de uso.

## EJERCICIO 3A: ¿Y si se acaban las pociones? 
El paso 10 asume que el Jugador siempre tiene pociones. Agrega una decisión antes de "Restaurar vida". 
¿En qué carril va la decisión? En el carril de RPG Manager, técnicamente el sistema valida las existencias.

Guarda 1: [tiene pociones > 0]  →  ¿a qué acción va? A la acción "Restaurar vida del Personaje".

Guarda 2: [pociones == 0]  →  ¿a qué acción va? Salta la restauración y va directamente al rombo de Unión (paso 11) o muestra la acción "Informar: Sin pociones".

## BUG A CORREGIR 
Encuentra los tres errores de este diagrama de actividades: 
Un rombo "¿Tiene flechas?" con una sola salida etiquetada [sí]. 
Un fork abre dos caminos que terminan cada uno en su propio nodo final, sin join. 
La acción "Calcular daño al oponente" está en el carril del Jugador. 

# Error 1:
Decisión sin cobertura completa de guardas. Un rombo de decisión no puede tener solo una salida [sí]; debe incluir obligatoriamente todas las guardas posibles (en este caso, falta la salida [no] o [flechas == 0]).
# Error 2: 
Un nodo Fork (barra negra que abre caminos paralelos) debe converger obligatoriamente en un nodo Join antes de terminar. Dejar que cada rama termine por separado en su propio nodo final rompe el control de sincronización en UML. Un Fork (la barra negra horizontal o vertical) representa acciones que el sistema hace al mismo tiempo (en paralelo).
# Error 3: 
Acción ubicada en el carril incorrecto. La acción es una operación lógica/matemática que procesa el sistema, por lo que debe ubicarse en el carril del RPG Manager, no en el carril del Jugador.



# PREGUNTAS DE REFLEXIÓN 
## 1. ¿Por qué el diagrama de contexto no muestra la base de datos del RPG Manager si el sistema sí la usa? 
Porque el diagrama de contexto (nivel 0) trata al sistema completo como una caja negra. Su único objetivo es mostrar las entidades externas que están fuera de nuestro control y los datos que cruzan la frontera del sistema. La base de datos es un elemento interno e infraestructura propia del sistema, por lo que no se dibuja a este nivel (aparece más adelante, a partir de los DFD de nivel 1).

## 2. ¿Cuál es la diferencia entre el flujo de datos "datos del personaje" y el caso de uso "Crear Personaje"? 
- "Datos del personaje" es un flujo de datos (un sustantivo con información que viaja, como el nombre o la clase que el usuario introduce).
- "Crear Personaje" es un caso de uso (una meta funcional expresada como verbo + sustantivo que describe el objetivo que el jugador logra interactuando con el sistema).
En resumen: los datos son la información que se transporta, y el caso de uso es el proceso o funcionalidad que se ejecuta con ellos.
  
## 3. Da un ejemplo propio del RPG Manager de «include» y otro de «extend» que no estén en este taller. 
- Ejemplo de «include» (obligatorio): CU-Comprar en Tienda «include» CU-Verificar Saldo de Monedas. Cada vez que el jugador intenta comprar algo, el sistema siempre, obligatoriamente, tiene que verificar si le alcanza el dinero.
- Ejemplo de «extend» (opcional): CU-Combatir en la Arena «extend» CU-Invitar Amigo a Espectar. La invitación a un amigo es un comportamiento opcional que solo ocurre si el jugador decide hacerlo en medio del proceso.
- 
## 4. ¿Qué información aporta el diagrama de actividades que el de casos de uso no puede mostrar? 
El diagrama de casos de uso solo muestra qué puede hacer cada actor a grandes rasgos ("la foto general"). En cambio, el diagrama de actividades muestra el cómo paso a paso: detalla el flujo secuencial, las decisiones lógicas con sus respectivas guardas, los ciclos o bucles (como cuando se repiten las rondas de combate), el paralelismo (fork/join) y la distribución exacta de responsabilidades entre los carriles de los actores y el sistema.

## 5. El paso "Calcular daño al oponente" será un método en POO. ¿En qué clase crees que vive y por qué? 
Lo más probable es que viva en una clase de control de lógica como Combate o Batalla, o bien como parte de un servicio de reglas del juego. Porque para calcular el daño se necesitan los atributos de ambas partes (el ataque del atacante y la defensa del oponente). Poner este cálculo en una clase mediadora o controladora evita acoplar demasiado las clases individuales y mantiene una separación limpia de responsabilidades.

## 6. ¿Cuándo preferirías PlantUML y cuándo draw.io en un proyecto real? 
- Prefiero PlantUML cuando estoy trabajando en equipo dentro de un repositorio de código y necesito documentar rápido, ya que al escribirse como texto plano se versiona excelente en Git (git diff muestra exactamente qué línea cambió).
- Prefiero draw.io cuando necesito hacer presentaciones ejecutivas, explicar el sistema a clientes o usuarios no técnicos, o cuando requiero un control visual total sobre la estética, colores, tamaños y la posición exacta de cada figura.

## Autoevaluación
Marca con una **X** la opción que mejor represente tu nivel de comprensión.

| Tema | 😕 No entendí | 🙂 Más o menos | 😄 ¡Lo tengo! |
|---|:---:|:---:|:---:|
| Manejo básico de draw.io (figuras, conectores y guardar) | ☐ | ☐ | [x]|
| Diagrama de contexto y flujos de datos | ☐ | ☐ | [x] |
| Actores y casos de uso | ☐ | ☐ | [x] |
| «include», «extend» y generalización | ☐ | ☐ | [x] |
| Decisiones, guardas y carriles | ☐ | ☐ | [x] |
| Fork / Join | ☐ | [x] | ☐ |
| Exportar y versionar en GitHub | ☐ | ☐ | [x] |
