# Trezu — Copy para Reddit

---

## Post 1: r/web3 / r/CryptoCurrency — Presentación general

**Título:** Construimos una tesorería multisig cross-chain para equipos

---

Gestionar fondos cripto compartidos en un equipo sigue siendo un desastre.

La mayoría de los equipos termina con alguna de estas soluciones:
- Una persona tiene las claves y todos simplemente... confían en ella
- Un multisig básico donde las aprobaciones se coordinan por DMs y mensajes ignorados
- Planillas de cálculo rastreando quién aprobó qué, de forma manual

Construimos **Trezu** para resolver esto. Es una plataforma de tesorería no-custodial que permite a equipos gestionar cripto en más de 30 blockchains con separación de roles y trazabilidad on-chain.

**Cómo funciona:**
- **Requestors** proponen pagos o swaps — no pueden aprobar sus propias solicitudes
- **Finance** vota para aprobar o rechazar — no puede tocar la configuración de la tesorería
- **Governance** gestiona miembros y reglas de votación — no puede mover fondos

Toda acción requiere aprobación colectiva. Nada se ejecuta hasta alcanzar el umbral configurado.

Soportamos Ethereum, NEAR, Solana, Bitcoin, Polygon, Sui, TON, Cardano y más — todo desde una sola interfaz. Swaps cross-chain incluidos.

Si estás manejando una DAO, una startup Web3, o cualquier equipo con fondos cripto compartidos — nos encantaría tu feedback.

👉 https://docs.trezu.org

---

## Post 2: r/ethereum / r/nearprotocol — Técnico

**Título:** Construimos una tesorería multisig con roles y soporte cross-chain — así funciona el modelo de permisos

---

Lo que falta en la mayoría de los setups multisig es **separación de roles**.

Multisig estándar: N-de-M firmantes. Cualquiera propone, cualquiera aprueba. Está bien para uso personal, pero en equipos genera problemas: sin trazabilidad, sin separación de responsabilidades, fácil de saltear informalmente.

**Trezu** lo resuelve así:

```
Requestor  → puede proponer pagos/swaps, no puede votar
Finance    → puede aprobar/rechazar propuestas, no puede crearlas
Governance → controla configuración (miembros, umbrales, duración), no puede mover fondos
```

Los roles son aditivos — se pueden combinar. Pero la separación es intencional: quien solicita un pago nunca es quien lo aprueba (a menos que combines roles conscientemente).

En el lado técnico:
- No-custodial — los fondos permanecen on-chain bajo control del equipo
- Umbrales de votación configurables (ej: 3 de 5 miembros Finance)
- Duración de votación configurable
- Soporte para Ledger en firmantes críticos
- Libreta de direcciones para destinatarios frecuentes (reduce errores de copiar/pegar)
- Más de 30 chains: Ethereum, NEAR, Solana, Bitcoin, Polygon, Sui

Estamos en fase de documentación y recolectando feedback de DAOs y equipos Web3. Respondo preguntas técnicas con gusto.

👉 https://docs.trezu.org

---

## Post 3: r/DAO — Caso de uso

**Título:** Cómo estructurar la tesorería de una DAO con separación de roles real (usando Trezu)

---

La mayoría de las DAOs que conozco tiene uno de estos dos problemas:

1. Tesorería controlada por 2-3 founders con acceso total — punto único de falla y de confianza
2. Gobernanza on-chain completa para cada pago — tan lento que las operaciones se paralizan

Acá hay un punto medio que funciona bien:

**Estructura del equipo:**
- 2-3 wallets Governance en hardware (Ledger) — uso infrecuente, solo para cambios de configuración
- 3-5 miembros Finance para aprobaciones — umbral en 2/3 o 3/5
- Todos los contributors operativos como Requestors — proponen, Finance aprueba

**Flujo del día a día:**
1. Un contributor de ops envía una propuesta de pago con comentario/justificación
2. Finance revisa de forma asíncrona (ventana de votación: 24-48h)
3. Si se alcanza el umbral → se ejecuta automáticamente on-chain
4. Si se rechaza → los fondos nunca se mueven, el rechazo queda registrado con motivo

**Qué se gana:**
- Trazabilidad completa on-chain
- Ninguna persona puede mover fondos unilateralmente
- Los cambios de gobernanza (agregar miembros, cambiar umbrales) están separados de las operaciones financieras
- Operaciones cross-chain desde una sola interfaz — sin malabarismo con wallets por chain

Lo estamos construyendo con [Trezu](https://docs.trezu.org). Todavía temprano, nos interesa saber cómo otros están estructurando su tesorería.

---

## Post 4: r/Cripto — Comunidad hispanohablante

**Título:** Cómo nuestro equipo dejó de depender de una sola persona para mover los fondos cripto

---

Trabajamos en un proyecto Web3 y durante mucho tiempo tuvimos el problema que creo que tienen muchos equipos: los fondos del proyecto estaban en una wallet que manejaban 2 personas. Sin registro, sin trazabilidad, y con la incomodidad de que si alguno de los dos no estaba disponible, nada se podía mover.

Probamos distintas soluciones hasta que encontramos **Trezu**, una plataforma de tesorería multisig no-custodial que permite gestionar los fondos del equipo con roles separados.

La diferencia clave con un multisig común:

- Hay roles distintos para quien **propone** un pago y quien lo **aprueba**
- Quien administra la configuración (agregar miembros, cambiar reglas) **no puede mover fondos**
- Todo queda registrado on-chain: quién propuso, quién aprobó, cuándo se ejecutó

Para nosotros fue un cambio grande. Ahora cualquier miembro del equipo puede proponer un pago, pero siempre requiere que al menos 2 de los 3 responsables financieros aprueben antes de que se ejecute algo.

Funciona en más de 30 blockchains (NEAR, Ethereum, Solana, Bitcoin, entre otras) y tiene swap cross-chain incluido.

Si están manejando fondos en equipo y todavía lo hacen con una sola wallet o un multisig básico, vale la pena darle un vistazo.

👉 https://docs.trezu.org

---

## Tags sugeridos por post

- Post 1: `web3` `cripto` `multisig` `dao` `tesorería`
- Post 2: `ethereum` `near` `defi` `seguridad` `multisig`
- Post 3: `dao` `gobernanza` `tesorería` `web3` `cripto`
- Post 4: `cripto` `bitcoin` `ethereum` `web3` `finanzas`
