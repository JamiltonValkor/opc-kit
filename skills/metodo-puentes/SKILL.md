---
name: metodo-puentes
description: Método de Jamilton Valkor para construir con agentes de IA sin perder el rumbo del negocio. Lleva cualquier feature, mejora o lote de feedback por etapas (negocio → PUENTE negocio↔código → investigación del código con subagentes → decisiones técnicas → plan → implementación → pruebas que validan negocio → entrega verificada), con el OK de la persona dueña entre etapas. Úsala SIEMPRE que el usuario pida construir o cambiar algo de su producto, pegue feedback de pruebas o de clientes, diga "esto falló", "investiga y arregla", "quiero agregar…", "misma dinámica de siempre", o haya varios hallazgos a la vez, aunque no diga "método".
---

# Método de puentes

Convierte una idea o un lote de feedback en cambios verificados, sin que la persona
dueña del negocio (el *owner*) tenga que repetir contexto. Tú orquestas: entiendes,
investigas, decides lo técnico, llevas lo de negocio a conversación, repartes trabajo a
subagentes, revisas todo y reportas.

## La regla de oro: siempre el puente

Casi todo lo que sale mal con agentes de IA sale mal en un salto: de la idea de negocio
directo al código, o de la investigación directo a las tareas. **Entre cada etapa hay un
puente, y nunca se salta.** Un puente es:

1. **Traducir** lo que se decidió al idioma de la etapa siguiente (negocio → reglas del
   sistema → contratos → tareas → pruebas).
2. **Mostrarlo** al owner en lenguaje simple: «esto decidimos, así se traduce, esto NO se
   toca».
3. **Esperar su OK** antes de cruzar.

Si te das cuenta de que estás escribiendo código o tareas sin un puente aprobado detrás,
detente y vuelve al puente que falta. Esto vale también al final de cada respuesta larga:
cierra diciendo en qué puente quedaste y cuál es el siguiente.

Los puentes obligatorios:

| Puente | De → a | Qué se entrega |
|---|---|---|
| P1 | Feedback / idea → puntos de negocio | Lista numerada con las palabras del owner y su evidencia |
| P2 | Negocio → reglas del sistema (**el puente principal**) | Qué pasa en cada caso, qué ve el usuario, qué no se toca |
| P3 | Reglas → evidencia del código | Cómo funciona hoy, con `archivo:línea`; qué ya existe para reutilizar |
| P4 | Evidencia → decisiones técnicas → plan | Plan completo (back **y** front) que otro modelo podría ejecutar sin contexto oculto |
| P5 | Plan → código | Cada entrega revisada contra el plan aprobado |
| P6 | Código → reglas de negocio | Pruebas que responden «¿qué regla del negocio garantiza esto?» |
| P7 | Pruebas → entrega | Funcionando de verdad, con evidencia, y lo que quedó pendiente |

Lee `references/principios.md` antes de proponer nada y usa las plantillas de
`references/plantillas.md`.

## 0. Prepara el terreno (una vez por sesión)

- Busca o crea la carpeta de la ola de trabajo (por ejemplo `docs/tasks/<ola>/` con un
  `progress.md`). Anota ahí todo lo que hagas: es la memoria entre sesiones.
- Averigua cómo se prueba de verdad este proyecto (local, staging, datos de prueba) y
  qué está prohibido tocar (producción, credenciales, bases de datos con escritura).

## 1. Desarma en puntos (puente P1)

Numera cada hallazgo o pedido con las palabras del owner y su evidencia (captura, URL,
hora, ids). Un mensaje suele mezclar bugs, experiencia de usuario y preguntas: sepáralos.
No asumas: si una captura muestra un estado, ese estado es el dato.

## 2. Decisiones de negocio y el puente al sistema (P2)

Primero el negocio, sin hablar de código: qué se quiere, para quién, por qué y cómo
sabremos que funcionó. Es una conversación, no una tabla de "decide tú":

1. Lo que viste y lo que pasa de verdad (con evidencia).
2. Qué siente el usuario por esto.
3. **Tu propuesta y por qué**, concreta.
4. Alternativas reales con su costo.
5. Una pregunta abierta: «¿Cómo lo ves?».

Con el OK, cruza el puente principal: traduce cada decisión a **reglas del sistema**
(qué pasa en cada caso, qué ve el usuario, qué no se toca) y documéntalo como plan de
negocio (puedes usar la skill `create-implementation-plan` en modo negocio). **Nada de
código ni de agentes de implementación hasta que el owner apruebe estas reglas.**

## 3. Investiga el código con subagentes de solo lectura (P3)

Antes de decidir cómo se hace, entiende cómo funciona hoy lo que se va a tocar: quién
orquesta qué, qué ya existe para reutilizar y qué contratos hay.

- Por qué: los agentes asumen, reinventan y repiten código, y el sistema crece sin que
  nadie sepa qué hace cada cosa.
- Reparte puntos independientes entre subagentes de solo lectura con un brief acotado.
- Cada afirmación vuelve con evidencia (`archivo:línea`, log, fila). Lo que no se pudo
  probar se marca como hipótesis.
- Para bugs: pregunta «por qué» hasta llegar a algo accionable y distingue síntoma,
  factor contribuyente y causa raíz.

## 4. Decisiones técnicas y plan (P4)

Discusión técnica **solo con lo que mostró la investigación**. Decide tú los detalles
técnicos y preséntalos como recomendación; lleva como pregunta solo lo de negocio.

Después de la discusión, arma el plan con la skill `create-implementation-plan` (no a
mano) y audítalo:

1. Subagentes de solo lectura verifican que exista cada ruta o comando citado, agregan
   anclas exactas (`ruta:línea`) y sacan a la luz supuestos ocultos.
2. Un crítico revisa las anclas de mayor impacto y el contrato front↔back de punta a punta.
3. Lo que siga sin verificar pasa a ser un paso explícito de la primera tarea.

El plan es **completo**: back y front, ambos escritos antes de ejecutar. Preséntalo al
owner y espera su OK. Quién implementa (Claude, Codex, otro) lo decide el owner en cada ola.

## 5. Implementa con subagentes (P5)

- Lo que no tiene dependencias va en paralelo, en segundo plano, cada agente en su propio
  worktree o rama. Brief con la plantilla: problema verificado, lógica a reutilizar con
  rutas, qué NO tocar, pruebas y qué reportar.
- Cambios de comportamiento detrás de un flag cuando el riesgo lo pida.
- Micro-arreglos (una línea, un texto) hazlos tú.
- **Loops largos:** un agente atascado no avisa. Cada pocas horas pregúntale «¿cuánto
  vas?, ¿qué te bloquea?, ¿qué te va a frenar después?» y destrábalo.

## 6. Revisa cada entrega

Lee el diff completo antes de aceptar. Busca lógica inventada, principios rotos, cambios
fuera de alcance, pruebas que pasan por casualidad y flags que no apagan del todo. Corre
tú las pruebas. Si algo está mal, devuélveselo al agente con la corrección concreta.

## 7. Pruebas que validan negocio (P6)

Cada prueba responde «¿qué regla del negocio garantiza esto?». Prohibido inventar
pruebas que pasan solas o perseguir cobertura por cobertura. Prefiere pruebas de punta a
punta con datos reales cuando se pueda.

## 8. Entrega y cierra (P7)

Avisa al owner solo cuando todo esté verificado funcionando, con: qué quedó, dónde
probarlo, qué no cambia y qué quedó pendiente. Anótalo en `progress.md`. Nunca digas
"listo" con algo todavía en curso. Termina diciendo en qué puente quedó cada punto.
