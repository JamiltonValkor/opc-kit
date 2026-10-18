# Principios por defecto

Cada uno salió de un error real construyendo con agentes. Adáptalos a tu negocio: si el
owner ya decidió algo distinto, manda lo del owner. Anota aquí las reglas nuevas que
vayan saliendo.

## Producto

- **Tus usuarios no son técnicos.** Nada de códigos de error ni jerga en la pantalla.
  Mensajes simples y un solo botón de acción, solo cuando de verdad depende del usuario.
- **El sistema resuelve solo lo que no es culpa del usuario.** Reintentos y recuperación
  de fallas de terceros los hace el sistema, de forma acotada. El usuario no debería tener
  que volver a subir ni pulsar nada.
- **Una pieza nunca bloquea el resto.** Si una parte falla, las demás siguen.
- **Los revisores automáticos solo avisan.** Un evaluador de IA no descarta trabajo ni
  bloquea avanzar; sus hallazgos son sugerencias.
- **No perder trabajo del usuario.** Si algo falla, se conserva lo que eligió y se reintenta.
- **Validar requisitos antes, no después.** Si algo va a fallar por un requisito faltante,
  se detecta antes de gastar trabajo, y se bloquea solo con prueba de que falta.
- **Reutilizar la lógica que ya funciona** en vez de inventar flujos nuevos.
- **Nunca inventar** cifras, testimonios, descuentos ni resultados de pruebas.

## Operación y seguridad

- Trabaja en el ambiente de pruebas, nunca en producción, salvo que el owner lo diga.
- Bases de datos en solo lectura; las escrituras de datos las hace el owner.
- Nunca imprimas tokens ni secretos. Nunca cambies credenciales ni cuentas.
- Nunca saltes las validaciones del repositorio (nada de `--no-verify`).
- Si el owner no está: decide lo técnico; lo de negocio grande espera su OK.
