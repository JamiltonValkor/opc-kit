# Plantillas

## Puente (úsalo al cerrar cada etapa)

```
PUENTE <P#>: <de> → <a>
Lo que decidimos: <en lenguaje del owner>
Cómo se traduce: <reglas / contratos / tareas / pruebas>
Lo que NO se toca: <fuera de alcance>
Pendiente de tu OK: <una pregunta concreta>
```

## Conversación con el owner

Prosa conversacional, sin tablas de "decide tú". Por tema:

1. Lo que viste (en sus palabras) y lo que encontramos de verdad (evidencia simple).
2. Qué le pasa al usuario por esto.
3. **Mi propuesta y por qué** (concreta: qué vería el usuario).
4. Alternativas reales, si las hay, con su costo.
5. Pregunta abierta: «¿Cómo lo ves?».

Una tabla solo sirve como resumen final de estado, nunca para pedir decisiones.

## Documento de discusión

`docs/tasks/<ola>/discussion/<tema>.md`:

```
# <Tema>
## Qué vio el owner (sus palabras + evidencia)
## Qué encontramos (causa con evidencia: código/log/dato)
## Opciones
1. <opción> — pros / contras / costo
## Recomendación
## Decisión del owner (se llena después)
## Puente: cómo se traduce al sistema
```

## Brief para un subagente de investigación (solo lectura)

```
Investiga (solo lectura, sin escribir archivos ni datos) <punto>.
Evidencia de partida: <URL/ids/hora>. Busca en <repos/rama>.
Devuelve: cómo funciona hoy con evidencia (archivo:línea), causa raíz si es un bug,
y la lógica existente que serviría. Marca como hipótesis lo que no puedas probar.
```

## Brief para un subagente de implementación

```
Tarea <ID>. Ola: docs/tasks/<ola>/ — lee el plan y obedécelo.
Trabaja en tu propio worktree/rama: <comando>. No fusiones nada.

PROBLEMA (verificado): <ids, qué pasó, evidencia>
DECISIÓN DEL OWNER: <qué quiere y por qué>
REGLAS DEL SISTEMA (puente P2): <qué pasa en cada caso>
LÓGICA EXISTENTE A REUTILIZAR: <rutas:líneas>
HACER: <pasos>  ·  NO TOCAR: <fuera de alcance>
PRUEBAS: <casos de negocio>; corre las pruebas del área.
REPORTA: archivos, dónde vive el cambio (archivo:línea), salida de pruebas,
rama, ambigüedades (no adivines).
```

## Entrada de progreso

`docs/tasks/<ola>/progress.md`, al final:

```
## <fecha> <hora> — <tema>
- Puente actual: P<#>
- Causa / decisión: … (evidencia)
- Cambio: <rama>, pruebas …
- Estado: verificado funcionando / pendiente …
```
