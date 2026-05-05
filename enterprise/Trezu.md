# Trezu — Plataforma de Gestión de Tesorería Digital

## ¿Qué es Trezu?

**Trezu** es una plataforma no-custodial de gestión de tesorería en activos digitales diseñada para organizaciones que operan con criptomonedas. Permite a equipos financieros administrar fondos de forma segura, con controles de acceso basados en roles, flujos de aprobación auditables y soporte para múltiples redes blockchain desde una única interfaz.

A diferencia de las soluciones tradicionales de firma múltiple, Trezu incorpora **separación de funciones**, **trazabilidad completa** y **controles configurables**, respondiendo a los estándares de gestión de riesgo que las organizaciones requieren al operar con activos digitales.

---

## Propuesta de valor

| Necesidad organizacional | Solución Trezu |
|---|---|
| Evitar dependencia de una sola persona para mover fondos | Aprobación colectiva obligatoria con umbrales configurables |
| Separar quien solicita de quien autoriza pagos | Roles Requestor y Finance estructuralmente separados |
| Registrar y auditar cada movimiento de fondos | Trazabilidad completa on-chain de propuestas, votos y ejecuciones |
| Operar en múltiples redes sin multiplicar wallets | Gestión centralizada de 30+ blockchains desde una sola plataforma |
| Controlar quién puede modificar la configuración del sistema | Rol Governance independiente de las operaciones financieras |

---

## Funcionalidades principales

- **Pagos individuales y en lote**: emisión de órdenes de pago a una o múltiples cuentas externas con revisión previa a la ejecución
- **Intercambio de activos cross-chain**: conversión de activos entre blockchains directamente desde la tesorería, sin intermediarios externos
- **Staking institucional**: propuesta y gestión de posiciones de staking desde la tesorería colectiva
- **Gestión de accesos**: incorporación, modificación y desvinculación de miembros con asignación de roles específicos
- **Libreta de cuentas**: registro de direcciones de destino frecuentes vinculadas a múltiples redes, con validación previa al envío

---

## Modelo de control interno

Trezu implementa un esquema de **segregación de funciones** con tres roles diferenciados:

### Requestor — Iniciación
Responsable de generar solicitudes de pago, staking o intercambio. No posee capacidad de autorización. Puede cancelar sus propias solicitudes mientras estén pendientes.

### Finance — Autorización
Responsable de revisar, aprobar o rechazar las solicitudes generadas. No puede crear solicitudes ni modificar la configuración del sistema. Ejecuta las transacciones autorizadas.

### Governance — Administración
Responsable de la configuración del entorno: gestión de miembros, asignación de roles, definición de umbrales de aprobación y duración de los ciclos de votación. No tiene acceso a operaciones financieras.

> Este diseño responde al principio de **mínimo privilegio**: ningún miembro dispone de más permisos que los estrictamente necesarios para su función.

### Matriz de permisos

| Acción | Requestor | Finance | Governance |
|---|:---:|:---:|:---:|
| Crear solicitud de pago | ✅ | ❌ | ❌ |
| Autorizar / rechazar solicitud | ❌ | ✅ | ❌ |
| Gestionar miembros y roles | ❌ | ❌ | ✅ |
| Configurar umbrales y plazos | ❌ | ❌ | ✅ |
| Combinar con otros roles | ✅ | ✅ | ✅ |

---

## Flujo operativo de un pago

1. El **Requestor** genera una solicitud indicando cuenta de destino, activo y monto
2. Agrega justificación o documentación de respaldo para los autorizadores
3. La solicitud queda en estado pendiente y es notificada al equipo Finance
4. Los miembros Finance revisan y votan dentro del plazo configurado
5. Al alcanzar el umbral de aprobación, la transacción se ejecuta de forma automática

> ⚠️ Las transacciones ejecutadas son **irreversibles**. Una solicitud no puede modificarse tras su envío; solo puede cancelarse antes de ser autorizada.

---

## Controles de seguridad

**Firma múltiple (multisig)**
Ninguna transacción puede ejecutarse sin la firma de múltiples miembros autorizados. No existe una clave centralizada con control sobre los fondos.

**Modelo no-custodial**
Trezu no administra ni custodia los activos. Los fondos permanecen bajo el control directo de la organización en todo momento.

**Umbrales de aprobación configurables**
La organización define cuántas firmas son necesarias para autorizar una operación (por ejemplo: 3 de 5 miembros Finance).

**Plazos de votación configurables**
Se establece el período durante el cual una solicitud puede recibir votos antes de expirar.

**Compatibilidad con hardware wallets**
Soporte para dispositivos **Ledger**, recomendado para los roles de mayor responsabilidad dentro del esquema de control.

**Buenas prácticas recomendadas**
- Asignar el rol Governance exclusivamente a dispositivos de hardware compartidos entre miembros de confianza
- Revisar periódicamente la membresía activa y los roles asignados
- Configurar umbrales de aprobación acordes al nivel de riesgo de cada operación
- Mantener la separación entre roles de solicitud y autorización

---

## Redes soportadas

Trezu opera sobre **más de 30 redes blockchain**, entre ellas:

`Ethereum` · `NEAR` · `Solana` · `Bitcoin` · `Polygon` · `Sui` · `TON` · `Cardano` · `Avalanche` · `BNB Chain`

---

## Recursos

- Documentación técnica: https://docs.trezu.org
- Caso de uso: [[Trezu Enterprise - Caso de Uso]]

---

## Tags

#tesorería #activos-digitales #control-interno #multisig #web3 #enterprise #trezu #seguridad #gobernanza
