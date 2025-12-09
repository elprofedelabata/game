# Resumen del diseño del juego

## Concepto central
- Combates por turnos con estrategia y un equipo de siete heroes, cada uno ligado a un elemento unico (fuego, tierra, electrico, natura, agua, hielo, aire) y al color del arco iris.
- El jugador recorre un mapa y se enfrenta a enemigos a traves de estas batallas.

## Seleccion de personajes / progresión
- Hay 70 personajes (10 por elemento). El jugador elige uno por elemento y forma un equipo de siete.
- Las nuevas partidas desbloquean progresivamente personajes; no estan todos disponibles desde el principio.
- Al empezar una partida, el jugador elige un elemento y recibe tres personajes de ese elemento, repitiendo el proceso hasta cubrir los siete elementos.
- Entre los tres personajes ofrecidos, al menos uno sera un personaje que el jugador no haya jugado antes, siempre que existan candidatos sin probar.
- Rerolls: recurso global limitado y fijo, ganado al completar runs. Gastar uno ofrece tres personajes diferentes del elemento actual, manteniendo la garantia de nuevo personaje cuando sea posible.

## Roles
- Cinco categorias de rol que describen la especializacion de cada personaje (no clases rigidas):
  * DPS (infligir dano)
  * Tanque (absorber dano)
  * Sanador (recuperar PV o aplicar escudos)
  * Buff (conceder mejoras a aliados)
  * Debuff (provocar perjuicios o estados negativos en enemigos)
- Cada personaje muestra una distribucion porcentual de los cinco roles que suma 100 %, brindando una vision rapida de su funcion.
- Los elementos tienden a favorecer ciertos roles, pero cada elemento tiene personajes especializados en todas las categorias.

## Estadisticas de personaje
- Cada personaje tiene:
  * Puntos de vida (salud)
  * Potencia (capacidad de ataque)
  * Resistencia (capacidad defensiva)
  * Agilidad (movimiento)
  * Suerte (propiedad especial a detallar mas adelante)

Mas adelante definiremos con mayor detalle que efectos tienen Agilidad y Suerte en combate.

## Habilidades pasivas
- Cada personaje cuenta con una pasiva unica vinculada a su elemento, rol predominante y estadisticas.
- Algunas pasivas afectan solo al propio personaje (por ejemplo, bonificaciones de dano cuando esta solo o mejoras en regeneracion de salud).
- Otras pasivas benefician tambien al equipo (bonificaciones defensivas compartidas, curas cuando se cumplen condiciones, etc.).
- Estas pasivas se mantienen activas de forma individual; no hay pasivas globales del equipo, pero pueden interactuar de forma indirecta al complementar las estrategias de los heroes.

## Habilidades de clase
- Cada personaje dispone desde el comienzo del run de seis habilidades de clase únicas, para un total de 420 habilidades.
- Estas habilidades reflejan la identidad de su elemento, rol y estadísticas, y permiten variedad tanto en ataque como en soporte o control.
- Las habilidades pueden requerir recursos como puntos de acción o tener recargas, según la especificación futura del sistema de combate.

## Habilidades básicas
- Cada elemento aporta 40 habilidades básicas adicionales, por lo general sencillas aunque algunas serán específicas y complejas según el elemento.
- El jugador comienza la partida con un número fijo de habilidades básicas determinado por la clase del personaje.
- Las habilidades básicas concretas se seleccionan aleatoriamente durante la pantalla de selección del personaje, añadiendo variabilidad a cada run.

## Sistema de combate inicial
- El combate se desarrolla sobre un tablero de casillas cuadradas que representa un terreno físico (plaza, claro, etc.).
- Al activarse el combate se colocan los enemigos sobre casillas específicas y el jugador sitúa a los héroes en un área predefinida.
- El área de colocación es lo bastante amplia para ofrecer diversas formaciones estratégicas, pero lo bastante reducida para mantener la sensación de grupo compacto.

## Turnos y fases
- El combate avanza por turnos numerados (1, 2, 3, 4...) y termina cuando todos los miembros de un bando han sido derrotados.
- Cada turno se divide en cuatro fases: preparación, lanzamiento de dados de acción, combate y eventos. Las siguientes secciones desarrollan cada fase en detalle.

### Fase de preparación
- Cada jugador configura su dado de acción, que determina qué acción realizará durante la fase de combate.
- El dado tiene seis caras, asociadas a partes del cuerpo: cabeza, pecho, mano izquierda, mano derecha, piernas y pies.
- Durante la preparación, el jugador asigna sus habilidades (de clase y básicas) a las caras del dado según prefiera. Cada habilidad indica a qué caras se puede vincular; por ejemplo, un ataque con garras puede enlazarse a la mano izquierda y/o mano derecha, pero no a la cabeza.

### Fase de lanzamiento de dados de acción
- Los enemigos lanzan primero sus dados de acción, predefinidos según cada criatura, para que el jugador sepa qué acciones enfrentarán.
- Después el jugador lanza los dados de acción de sus personajes.
- El jugador puede reservar los dados cuyo resultado quiere usar y relanzar los demás. Cada personaje puede lanzar su dado una cantidad de veces igual a su estadística de suerte; la tirada inicial cuenta como una de esas oportunidades, por lo que suerte nunca puede ser menor a 1.
- Cuando todos los dados están reservados o se agotan las tiradas disponibles, se pasa a la fase de combate.

## Objetos y acciones
- Los personajes pueden portar objetos que, además de sus estadísticas o usos pasivos, pueden traer acciones asociadas que se cargan en el dado de acción.
- Cada acción de objeto indica las caras del dado a las que puede asignarse. Por ejemplo, una espada puede incluir la acción “espadazo” enlazable a mano izquierda y/o mano derecha.
- Una poción podría ofrecer dos acciones diferenciadas: “beber poción” (cabeza) y “lanzar poción” (mano izquierda/ derecha), dándole versatilidad táctica al objeto.

## Fase de combate
- Cada acción definida por una habilidad o un objeto especifica un MOMENTO en el que tiene lugar: un valor entre 0 y 9 o infinito.
- El orden de ejecución sigue los momentos de menor a mayor. Las acciones con momento 0 (inicio) se ejecutan antes de que el resto del turno comience.
- Para momentos 1-9, se ejecutan todas las acciones del momento actual ordenadas por la AGILIDAD del ejecutor (más ágil primero). En caso de empate, los aliados actúan antes que los enemigos.
- Tras completar todas las acciones del momento 9, se procesan los momentos infinitos (final del turno), que cubren efectos que deben ocurrir al cierre del turno o justo después de los demás momentos.

### Actuación de aliados y enemigos
- Cuando llega su momento de actuar, cada personaje (aliado o enemigo) puede moverse hasta un número de casillas igual a su AGILIDAD antes o después de ejecutar su acción elegida.
- El movimiento y la acción pueden ordenarse a voluntad del jugador o del controlador de enemigos, lo que permite maniobrar para posicionarse o aprovechar zonas de efecto.

### Tipos de acciones
- Las acciones disponibles en el dado se dividen en dos clases:
  * Acciones enfrentadas: requieren una tirada enfrentada entre quien ejecuta la acción y quien la recibe (por ejemplo, ataques o habilidades de control). El resultado de dichas tiradas decidirá si la acción impacta y qué efectos produce.
  * Efectos automáticos: se aplican directamente sin necesidad de resolución competitiva, como curaciones, bonos defensivos o acumulaciones de recursos.

Paso siguiente: detallar cómo funcionan las acciones enfrentadas.

### Acciones enfrentadas
- Se lanza un número de dados de 6 caras igual al valor de POTENCIA del atacante.
- El defensor lanza dados igual a su RESISTENCIA; si hay múltiples objetivos para una sola acción, se toma la resistencia más alta y se suma 1 por cada objetivo adicional.
- Los dados del atacante cancelan a los del defensor igualando o superando sus valores. Un ataque puede combinar varios dados para anular un dado defensivo, pero cada dado defendido solo puede ser anulado una vez y no hay efecto colateral para los dados restantes.
- Tras anular, se evalúa el resultado:
   * Si quedan dados del atacante sin cancelar → ÉXITO ABSOLUTO.
   * Si no quedan dados de ninguno de los bandos → ÉXITO.
   * Si quedan 1 o 2 dados del defensor → ÉXITO PARCIAL.
   * Si quedan 3 o más dados del defensor → FRACASO ABSOLUTO.

### Ejemplo de resultados
- Cada acción enfrentada determina qué efecto produce según el grado de éxito alcanzado.
- Por ejemplo, la habilidad “Proyectil de fuego” podría tener este desglose:
  * ÉXITO ABSOLUTO: inflige 40 de daño de fuego y aplica el estado QUEMADO.
  * ÉXITO: inflige 30 de daño de fuego.
  * ÉXITO PARCIAL: inflige 10 de daño de fuego.
  * FRACASO ABSOLUTO: el atacante recibe 30 de daño.
- Algunas acciones no contemplan todos los niveles de éxito (solo ÉXITO/FRACASO) o simplemente no ejecutan efecto ante el fracaso.
- Además de los resultados enfrentados también existe el caso de `efecto_automatico`, que describe una acción que se aplica sin enfrentamiento (habilidades automáticas, pasivas de área o acciones de objetos que no se contraponen).  

### Armadura
- Los personajes pueden acumular ARMADURA mediante habilidades, objetos, pasivas o eventos durante el combate.
- La armadura se mantiene mientras no se elimine explícitamente y sólo se consume al intentar acciones enfrentadas: antes de lanzar dados de resistencia, primero se debe anular la armadura con los dados disponibles del atacante.
- La armadura se neutraliza mediante dados del atacante; cada dado solo puede usarse una vez y se elimina tras su uso. Por ejemplo, si el defensor tiene 5 de armadura y el atacante saca 4, 4, 3, 2 y 2, lo óptimo sería consumir los dados de 3 y 2 (sumando 5) para derribar ese valor antes de seguir contra la resistencia.
- Algunas acciones específicas pueden dañar o reducir armadura sin implicar daño directo, permitiendo eliminar este buffer defensivo para hacer después un ataque normal.

## Fase de eventos
- Al final de cada turno tiene lugar la fase de eventos. Esta fase sirve para introducir efectos ambientales, narrativos o estratégicos que no forman parte de las acciones normales de los combatientes.
- Los eventos pueden depender del área donde transcurre el combate (un bosque, la plaza de una ciudad, etc.), activar condiciones nuevas (tormentas, lluvia de meteoros, refuerzos enemigos) o avanzar instancias de la historia (como la aparición de un jefe o diálogos clave).
- Algunos eventos pueden tener impacto permanente en el combate (añadir estados, cambiar terreno, activar buffs/debuffs), otros simplemente narran sucesos y otros pueden alterar los recursos disponibles de los personajes.
- La fase de eventos también es útil para ejecutar mecánicas repetitivas con temporizadores (por ejemplo, “cada tercer turno cae una tormenta” o “a partir del turno 5 un enemigo especial se une”). Podremos definir plantillas de evento por tipo de mapa cuando especifiquemos los encuentros concretos.

## Estructura de datos
- Para mantener organizados los personajes y habilidades, podemos guardar los registros en JSON dentro de `data/`.
- Por ejemplo, `data/habilidades_clase.json` y `data/habilidades_basicas.json` almacenan los 6 ataques únicos por personaje y las 40 habilidades básicas por elemento siguiendo una ficha común (identificador, elemento, tipo, momento, distribución de rol y efectos por resultado).
- Más adelante podemos añadir `data/personajes.json`, `data/pasivas.json` u otros archivos similares para tener la información lista para uso en prototipos o herramientas.
- Dentro de la estructura de habilidades también incluimos un `enfriamiento` (cooldown) que indica cada cuántos turnos se puede volver a usar la acción. Por ejemplo, `enfriamiento: 2` significa que la habilidad puede ejecutarse un turno sí, luego hay que esperar dos turnos completos antes de volver a lanzarla, y así sucesivamente.
- En `data/personajes.json` podemos usar un campo `beneficios` (lista) que recoja ventajas permanentes como inmunidades de elemento o clase. Esto servirá para documentar reglas como “los personajes de fuego no pueden ser quemados” o “los elementales de roca no sangran”, mientras que otros personajes pueden dejarlo en blanco.

## Mecánicas y estados elementales
- Cada uno de los siete elementos tendrá una mecánica asociada y un estado alterado característico; iremos llenando esta sección a medida que definamos cada elemento.
- **Fuego**: mecánica “Sacrificio” (algunas habilidades ganan potencia adicional a cambio de un perjuicio como perder PV o sufrir efectos), estado “Quemadura” (el objetivo recibe 10 daño fuego al final del turno y pierde 1 de potencia mientras dura).
- **Tierra**: mecánica pendiente; estado “Fango” (el dado de acción del objetivo no puede relanzarse correctamente y repite la última cara obtenida; si aún no se ha lanzado el dado, se muestra una cara aleatoria y ya no puede volver a lanzarse).
- **Eléctrico**: mecánica “En cadena” (algunas habilidades ganan beneficios si algún aliado actúa en el mismo momento que la acción o afectan a objetivos adyacentes formando una cadena), estado “Parálisis” (reduce a 1 la AGILIDAD del objetivo y anula su próximo desplazamiento).
- **Natura**: mecánica “Drenaje” (algunas habilidades sanan al atacante cuando infligen daño), estado “Veneno” (inflige 10 daño natura al final del turno y reduce en 1 la RESISTENCIA del objetivo mientras dure).
- **Agua**: mecánica “Mimetismo” (algunas habilidades imitan efectos o propiedades de acciones ejecutadas antes), estado “Humedad” (detalle en desarrollo).
- **Hielo**: mecánica “Congelación” (aún por definir), estado “Fragilidad” (en una tirada de resistencia el mayor dado se sustituye por un 1).
- **Aire**: mecánica “Soplo” (algunas habilidades reposicionan el dado de acción si cae en ellas, mecánica a pulir), estado “Vértigo” (en una tirada enfrentada de potencia, un dado del mayor valor se sustituye por un 1).
- **Roles de ejemplo**: Pierre se diseña como 70% DPS, 0% Tanque, 0% Sanador, 10% Buffer y 20% Debuffer, reflejando su énfasis en daño y quemaduras con una pizca de apoyo y control de estados.
