# Kit One Person Company · EFFIX 2026

**Una persona al frente. Un equipo de IA para construir el negocio.**

Estos son los recursos de la charla *One Person Company* de **Jamilton Valkor** (Founder CTO/CPO de [SaleADS.ai](https://saleads.ai)). Aquí está lo mismo que viste en el escenario: el método, el plan, el consejo de advisors y la tropa entera de agentes para armar tu propia empresa de una persona.

> Sígueme en redes como **@JamiltonQO**. Ahí comparto el proceso de lo que construyo.

---

## Cómo instalar en 1 minuto

Necesitas [Claude Code](https://claude.com/claude-code) (o Codex, Cursor u otro agente compatible con *Agent Skills*).

```bash
npx skills add JamiltonValkor/opc-kit -a claude-code
```

Eso instala las dos skills de este repo. Si prefieres hacerlo a mano:

```bash
git clone https://github.com/JamiltonValkor/opc-kit
cp -r opc-kit/skills/* ~/.claude/skills/
```

---

## 1. Mi método: `metodo-puentes`

Es la forma en que construyo con agentes de IA todos los días, abierta para cualquier negocio.

La idea central: **casi todo lo que sale mal con la IA sale mal en un salto**. Se salta de la idea directo al código, o de la investigación directo a las tareas. Por eso, entre cada etapa hay un **puente**: se traduce lo decidido al idioma de la siguiente etapa, se muestra en lenguaje simple y se espera tu OK.

```
negocio → PUENTE negocio↔sistema → investigación del código → decisiones técnicas
→ plan → implementación con subagentes → pruebas que validan negocio → entrega verificada
```

Úsala diciéndole a tu agente: *"quiero agregar…"*, *"esto falló, investiga y arregla"* o *"misma dinámica de siempre"*.

📁 [`skills/metodo-puentes`](skills/metodo-puentes/SKILL.md)

## 2. El plan de implementación: `create-implementation-plan`

Convierte una idea aprobada en un paquete de tareas tan claro que **otro modelo lo puede ejecutar sin contexto oculto**. Cada tarea trae qué hacer, qué no tocar, criterios de aceptación y plan de pruebas. El método de puentes la usa en los pasos 2 y 4.

Créditos: skill original de **Leonardo González**, del proyecto [OpenSymphony](https://github.com/kumanday/OpenSymphony) (licencia MIT).

📁 [`skills/create-implementation-plan`](skills/create-implementation-plan/SKILL.md)

## 3. El consejo: LLM Council

No le preguntes a una sola IA. Esta skill pone a **cinco advisors a debatir tu idea**, se revisan entre ellos y te entregan un veredicto. Úsala con *"council this"* o *"pressure-test this"*.

👉 [github.com/aiwithremy/claude-skills-llm-council](https://github.com/aiwithremy/claude-skills-llm-council)

Para instalarla, abre Claude y dile: *"Instala esta skill: https://github.com/aiwithremy/claude-skills-llm-council"*.

---

## 4. La tropa completa para tu One Person Company

Así se arma el enjambre de la charla (**1 + N**): tú en el centro, una junta directiva que te asesora y un equipo de agentes por área. Estos tres repositorios son abiertos (MIT) y no son míos. Te digo cuál usar para cada parte.

### Tú: la visión

Tú decides qué se construye y por qué. Tus agentes no te reemplazan: te multiplican.

### La junta directiva: CEO, CTO, CFO, CMO, COO y más

**[alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills)**, paquete *C-level*. Trae advisors de **CEO, CTO, CFO, CMO, COO, CPO, CRO, CHRO, CISO** y más, además de reuniones de junta y registro de decisiones.

```
/plugin marketplace add alirezarezvani/claude-skills
/plugin install c-level-skills@claude-code-skills
```

*(Escríbelo dentro de Claude Code.)*

### El equipo por áreas: la tienda de Daniela, versión agentes

**[msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents)** (*The Agency*): cientos de agentes especialistas, cada uno con su rol, su proceso y sus entregables.

| Área del negocio | Agentes de *The Agency* para empezar |
|---|---|
| Marketing | Growth Hacker, Content Creator, SEO Specialist, Email Marketing Strategist |
| Ventas | Outbound Strategist, Discovery Coach, Deal Strategist, Proposal Strategist |
| Postventa y soporte | Support Responder |
| Finanzas | Finance Tracker, Bookkeeper & Controller, Financial Analyst, Tax Strategist |
| Operación | Operations Manager, Analytics Reporter |
| Legal | Legal Compliance Checker |

Instalación: en Mac, `brew install --cask msitarzewski/agency-agents/agency-agents`. También puedes clonar el repo y correr `./scripts/install.sh --tool claude-code`, o copiar a `~/.claude/agents/` solo los archivos que quieras.

### El área de marketing, a fondo

**[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills)**: 50 skills de copy, SEO, anuncios, *cold email*, conversión, precios y lanzamientos.

```bash
npx skills add coreyhaines31/marketingskills -a claude-code
```

### Mi consejo para empezar

No instales todo el primer día. **Elige un proceso donde hoy tú seas el cuello de botella**, ponle un agente y dirígelo con el método de puentes. Cuando funcione, sumas el siguiente.

> **El límite de tu negocio ya no es lo que alcanzas a hacer. Es lo que aprendes a dirigir.**

---

Hecho para la charla *One Person Company* · EFFIX 2026 · **@JamiltonQO**
