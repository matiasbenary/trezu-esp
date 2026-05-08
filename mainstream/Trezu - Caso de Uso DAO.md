# Trezu — Caso de Uso: DAO de protocolo DeFi

## Contexto

**NovaDeFi DAO** es una organización descentralizada que gestiona un protocolo de lending en NEAR y Ethereum. El equipo tiene 12 miembros distribuidos globalmente y maneja una tesorería de ~$2M en activos (NEAR, ETH, USDC).

Antes de Trezu, los fondos eran controlados por una sola wallet multisig gestionada informalmente, con acceso compartido entre los founders. El problema: falta de trazabilidad, dependencia de 2 personas para aprobar todo, y sin separación de roles.

---

## Estructura del equipo en Trezu

| Miembro | Rol en la DAO | Rol en Trezu |
|---|---|---|
| Alice (CTO) | Co-founder técnico | Governance + Finance |
| Bob (CEO) | Co-founder operativo | Governance |
| Carol (CFO) | Responsable financiera | Finance |
| Dave (Ops) | Operaciones | Requestor |
| Eve (Marketing) | Growth | Requestor |
| Frank (Dev) | Contributor | Requestor |

**Configuración de votación:** 2 de 3 miembros Finance deben aprobar para ejecutar cualquier pago.
**Duración de votación:** 48 horas.

---

## Escenario 1: Pago mensual a contributors

### Situación
Dave (Ops) necesita procesar los pagos mensuales a 8 contributors por un total de 15,000 USDC en NEAR.

### Flujo

```
Dave (Requestor)
  └── Crea propuesta "Pagos contributors - Mayo 2025"
        ├── Destinatario 1: wallet-contributor-1.near → 2,000 USDC
        ├── Destinatario 2: wallet-contributor-2.near → 1,500 USDC
        └── ... (8 pagos en una sola propuesta múltiple)
              └── Agrega comentario: "Según planilla aprobada en Discord"

Carol (Finance)
  └── Revisa propuesta, verifica montos contra planilla
        └── Vota ✅ APROBAR

Alice (Finance)
  └── Confirma con Carol, revisa wallets destinatarias
        └── Vota ✅ APROBAR → umbral alcanzado (2/3)

Sistema
  └── Ejecuta los 8 pagos automáticamente on-chain ✅
```

**Resultado:** Los 8 contributors reciben sus pagos sin que ningún individuo haya tenido control unilateral. Todo el proceso queda registrado on-chain.

---

## Escenario 2: Rebalanceo de activos entre chains

### Situación
La tesorería tiene exceso de ETH en Ethereum y necesita liquidez en NEAR para gastos operativos del mes.

### Flujo

```
Dave (Requestor)
  └── Crea propuesta de swap: 5 ETH → NEAR equivalente
        └── Comentario: "Rebalanceo para cubrir opex Q2"

Carol + Alice (Finance)
  └── Aprueban el swap (2/2 en 6 horas)

Trezu
  └── Ejecuta el swap cross-chain directamente desde la treasury
        └── Fondos disponibles en NEAR sin mover manualmente entre wallets ✅
```

---

## Escenario 3: Incorporación de nuevo miembro Finance

### Situación
La DAO vota incorporar a Grace como nueva miembro del equipo Finance para descentralizar las aprobaciones.

### Flujo

```
Bob (Governance)
  └── Crea propuesta de gobernanza: agregar wallet de Grace con rol Finance

Alice (Governance)
  └── Aprueba el cambio de configuración

Trezu
  └── Agrega a Grace como Finance
        └── Umbral de votación actualiza a: 2 de 4 Finance ✅
```

> ⚠️ Este cambio lo gestiona Governance, completamente separado de las operaciones financieras. Dave, Carol y Eve (Requestors/Finance) no intervienen en la configuración.

---

## Escenario 4: Propuesta rechazada

### Situación
Eve (Marketing) propone un pago de 50,000 USDC para una campaña de influencers sin aprobación previa del equipo.

### Flujo

```
Eve (Requestor)
  └── Crea propuesta: 50,000 USDC → wallet-agency.eth
        └── Comentario: "Campaña Q3 - ver brief en Notion"

Carol (Finance)
  └── Revisa: monto no estaba en el presupuesto aprobado
        └── Vota ❌ RECHAZAR con comentario: "No aprobado en budget Q3"

Alice (Finance)
  └── Vota ❌ RECHAZAR

Sistema
  └── Propuesta rechazada. Fondos nunca se movieron. ✅
```

**Resultado:** El sistema de aprobaciones actuó como control interno. El rechazo queda registrado con justificación.

---

## Escenario 5: Pagos confidenciales a auditores de seguridad

### Situación
NovaDeFi DAO contrata una auditoría de seguridad a una firma externa. El equipo no quiere exponer públicamente el monto ni la identidad del auditor hasta que la auditoría esté completa (para evitar que actores maliciosos anticipen vulnerabilidades en revisión).

### Solución
El equipo crea una **tesorería confidencial** separada para este tipo de pagos sensibles. Toda la información financiera es visible únicamente para los miembros del equipo; nada es público on-chain.

### Flujo

```
Alice (Governance) — tesorería pública
  └── Aprueba transferir 30,000 USDC al fondo de auditorías

[Fondeo de la tesorería confidencial vía near.com]
  └── Carol navega a near.com
        ├── Deposita 30,000 USDC desde su wallet
        ├── Mueve los fondos al shard privado (To Confidential)
        └── Envía los fondos a la cuenta near.com de la tesorería confidencial

Dave (Requestor) — tesorería confidencial
  └── Crea propuesta de pago: 30,000 USDC → cuenta near.com del auditor
        └── Comentario: "Auditoría de seguridad - contrato #AUD-2025-003"

Carol + Alice (Finance)
  └── Aprueban el pago confidencial (2/2 en 12 horas)

Auditor externo
  └── Recibe los fondos en su cuenta near.com
        └── Retira a su wallet externa desde near.com cuando corresponda
```

**Resultado:** El pago se procesó completamente en privado. Ningún actor externo conoce el monto, el destinatario ni la fecha de ejecución. El equipo mantiene trazabilidad interna completa.

> ⚠️ Para fondear una tesorería confidencial se debe usar [near.com](https://near.com/) como intermediario, ya que los shards privados no pueden recibir transacciones públicas directas.

---

## Beneficios observados vs. situación anterior

| Aspecto | Antes (multisig informal) | Con Trezu |
|---|---|---|
| Trazabilidad | Manual, en hojas de cálculo | Automática, on-chain |
| Aprobaciones | 2 founders con acceso total | Roles separados, 2 de 3 Finance |
| Riesgo de error | Alto (copiar/pegar wallets) | Bajo (Address Book + revisión) |
| Tiempo de pago | 2-3 días (coordinación manual) | ~6-48 horas (votación asíncrona) |
| Onboarding de nuevos aprobadores | Complejo y riesgoso | Controlado por Governance |
| Auditoría | Inexistente | Registro completo on-chain |
| Privacidad financiera | Inexistente | Opcional vía tesorería confidencial |

---

## Configuración recomendada para DAOs similares

```
Treasury NovaDeFi (Pública — operaciones diarias)
├── Governance: 2-3 wallets de hardware (Ledger)
├── Finance: 3-5 miembros, umbral 2/3 o 3/5
├── Requestors: todos los contributors con permisos operativos
├── Voting duration: 24-48h (equilibrio entre agilidad y seguridad)
└── Address Book: todas las wallets recurrentes pre-registradas

Treasury NovaDeFi Confidential (para pagos sensibles)
├── Mismos miembros Governance y Finance que la tesorería pública
├── Fondeo exclusivamente via near.com (shard privado)
├── Usar para: auditorías, acuerdos pre-anuncio, pagos estratégicos
└── Balances y transacciones visibles solo para el equipo
```

