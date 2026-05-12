# ¿Tu equipo maneja cripto? Así es como Trezu resuelve el caos de las wallets compartidas

Si alguna vez intentaste coordinar fondos cripto entre varias personas, sabés lo que es el problema.

Alguien tiene la seed phrase. Otro tiene acceso a la exchange. Un tercero "sabe cómo hacer el swap". Y cuando llega el momento de ejecutar un pago, hay tres conversaciones de Telegram abiertas, dos Notion con instrucciones contradictorias y, si tenés suerte, no terminó nadie enviando fondos a la dirección equivocada.

Esto no es un problema menor. Es el día a día de cientos de DAOs, startups Web3 y fondos de inversión cripto que siguen gestionando su tesorería de forma artesanal.

**Trezu existe para cambiar eso.**

---

## Una sola interfaz para todos tus activos multi-chain

Trezu es una plataforma no-custodial de gestión de tesorería que permite a equipos administrar activos cripto de forma colaborativa. La idea central es simple pero poderosa: **ningún miembro puede actuar unilateralmente**. Toda acción requiere el consenso del equipo.

Soporta más de 30 redes —Ethereum, NEAR, Solana, Bitcoin, Polygon, Sui, entre otras— desde una única interfaz. Sin wallets separadas por blockchain. Sin saltar entre apps. Sin perder el hilo.

---

## El problema de fondo: confianza sin control

En los modelos tradicionales de multisig, la seguridad depende de que todos los firmantes actúen bien. Pero no hay estructura que defina *quién puede proponer* un pago y *quién debe aprobarlo*. Esa ambigüedad genera fricciones, errores y, en el peor caso, fraudes internos.

Trezu resuelve esto con un **sistema de roles separados e intencionales**:

- **Requestor**: propone pagos, swaps o stakings. No puede votar ni aprobar nada.
- **Finance**: aprueba o rechaza propuestas. No puede crearlas ni tocar la configuración.
- **Governance**: administra miembros, roles y umbrales. No puede mover fondos.

El principio es de *mínimo privilegio*: cada persona tiene exactamente el acceso que necesita y nada más. El que propone no aprueba. El que aprueba no configura. Es separación de poderes aplicada a la tesorería.

---

## Cómo fluye una propuesta de pago

El flujo es deliberadamente simple:

1. El **Requestor** crea una propuesta: wallet destino, token, monto, comentario opcional.
2. La propuesta queda visible para el equipo **Finance** en estado pendiente.
3. Los miembros Finance **votan** durante el período configurado.
4. Al alcanzar el umbral de aprobación, la transacción **se ejecuta automáticamente**.

Nada de Telegram. Nada de "¿ya firmaste vos?". Nada de dudas sobre qué aprobaron realmente.

> ⚠️ Una vez aprobada, la transacción es irreversible. Por eso el flujo de revisión existe: para que nadie se arrepienta después.

---

## Tesorerías públicas y confidenciales

Uno de los features más interesantes de Trezu es la posibilidad de elegir entre dos tipos de tesorería al momento de crearla.

La **tesorería pública** opera sobre un contrato multisig en NEAR Protocol. Balances, transacciones y propuestas son visibles en la blockchain. Ideal para DAOs que quieren transparencia total con su comunidad.

La **tesorería confidencial** es otra historia. Está desplegada en un shard privado de NEAR: misma tecnología de seguridad, pero con toda la información financiera visible *únicamente para los miembros del equipo*. Balances, propuestas, historial de pagos: nada de eso es público.

Esto abre Trezu a organizaciones que, por razones competitivas, legales o simplemente de privacidad, no pueden (ni quieren) exponer sus movimientos financieros. Un fondo de inversión cripto, por ejemplo, no tiene ningún incentivo para que el mercado vea cada transacción que ejecuta.

---

## No-custodial: los fondos siempre son tuyos

Trezu no toca tu dinero. No hay intermediario. Los fondos permanecen bajo control del equipo en todo momento, respaldados por firmas individuales de cada miembro con su propia wallet.

Podés usar **Ledger** para los roles más críticos, configurar cuántas firmas se necesitan para aprobar una transacción (ej: 3 de 5 miembros Finance), y definir por cuánto tiempo permanece abierta una votación antes de expirar.

---

## ¿Para quién es Trezu?

Para cualquier equipo que maneje fondos cripto de forma colectiva y quiera dejar de improvisar:

- **DAOs** que necesitan gobernanza on-chain transparente
- **Startups Web3** con co-founders que quieren control compartido sin fricciones
- **Fondos de inversión cripto** que necesitan separación de roles real
- **Equipos de protocolo** que pagan a contributors regularmente
- **Empresas que operan en cripto** y necesitan flujos de aprobación internos

---

## La tesorería como infraestructura, no como workaround

El dinero de un equipo es su combustible. Gestionarlo con Telegram, spreadsheets y wallets personales es como construir infraestructura sobre arena.

Trezu propone algo distinto: una capa de gestión financiera diseñada desde cero para equipos descentralizados, con los controles, la transparencia y la privacidad que cada organización necesita.

Si tu equipo ya maneja cripto, la pregunta no es si necesitás algo así. La pregunta es cuánto tiempo más van a seguir sin tenerlo.

---

*Explorá Trezu en [docs.trezu.org](https://docs.trezu.org)*
