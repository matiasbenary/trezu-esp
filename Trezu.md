# Trezu

## ¿Qué es?

**Trezu** es una plataforma **no-custodial de gestión de tesorería multi-chain** que permite a equipos administrar activos cripto de forma colaborativa mediante un sistema de billetera compartida y control colectivo.

A diferencia de una billetera individual, en Trezu **ningún miembro puede actuar unilateralmente**: toda acción requiere consenso del equipo. Está diseñada para organizaciones que necesitan transparencia, trazabilidad y seguridad en el manejo de fondos digitales.

> "Una treasury es una billetera compartida que permite a equipos gestionar activos cripto en múltiples blockchains de forma segura." — Trezu Docs

---

## ¿Para qué sirve?

Trezu resuelve el problema de **gestionar fondos cripto en equipo sin sacrificar seguridad ni descentralización**:

- **Centralizar activos multi-chain** en una sola interfaz (sin necesitar wallets separadas por red)
- **Requerir múltiples aprobaciones** antes de ejecutar cualquier transacción
- **Separar responsabilidades** entre quien propone pagos, quien los aprueba y quien administra la configuración
- **Registrar y auditar** cada propuesta, voto y acción ejecutada
- **Delegar sin perder control**: los miembros operan dentro de los límites de su rol

### Operaciones soportadas

| Operación | Descripción |
|---|---|
| Pagos individuales | Transferir tokens a una wallet externa |
| Pagos múltiples | Enviar fondos a varios destinatarios en una sola propuesta |
| Swap de activos | Intercambiar tokens entre blockchains directamente desde la treasury |
| Staking | Proponer staking de activos desde la treasury |
| Gestión de miembros | Agregar, remover o modificar roles de miembros |

---

## Usuarios objetivo

Trezu está orientado a cualquier **equipo u organización que maneje fondos cripto de forma colectiva**:

- **DAOs**: gobernanza descentralizada de tesorería on-chain
- **Startups Web3**: control compartido de fondos operativos entre co-founders
- **Fondos de inversión cripto**: supervisión multifirma con separación de roles entre analistas y aprobadores
- **Equipos de protocolo**: administración de reservas y pagos a contributors
- **Empresas que pagan en cripto**: flujo de pagos con aprobaciones internas antes de ejecutar

---

## Modelo de gobernanza y roles

Trezu implementa un sistema de **roles separados e intencionales**. Cada miembro tiene una wallet propia y firma de forma independiente. Los roles se pueden combinar.

### Roles disponibles

**Requestor**
- Crea propuestas de pago, staking o swap
- Puede eliminar sus propias propuestas pendientes
- **No puede votar** ni aprobar propuestas

**Finance**
- Aprueba o rechaza propuestas creadas por Requestors
- Ejecuta las transacciones aprobadas
- **No puede crear propuestas** ni modificar configuración

**Governance**
- Administra la configuración de la treasury: miembros, roles, umbrales de votación, duración de votaciones
- **No puede crear propuestas financieras** (separación intencional de poderes)
- Rol de alto riesgo: se recomienda asignarlo solo a wallets de alta seguridad (ej: hardware wallets)

> El principio de diseño es **mínimo privilegio**: cada rol hace exactamente lo que necesita y nada más.

### Matriz de permisos

| Acción | Requestor | Finance | Governance |
|---|:---:|:---:|:---:|
| Crear propuesta de pago | ✅ | ❌ | ❌ |
| Aprobar / rechazar propuesta | ❌ | ✅ | ❌ |
| Gestionar miembros y roles | ❌ | ❌ | ✅ |
| Configurar umbrales de votación | ❌ | ❌ | ✅ |
| Combinar con otros roles | ✅ | ✅ | ✅ |

---

## Flujo de una propuesta de pago

1. **Requestor** navega a Pagos, ingresa wallet destinataria, token y monto
2. Agrega comentario opcional para los aprobadores y revisa antes de enviar
3. La propuesta queda en estado **pendiente** y es visible para el equipo Finance
4. Los miembros Finance **votan** a favor o en contra durante el período configurado
5. Al alcanzar el **umbral de aprobación**, la transacción se ejecuta automáticamente

> ⚠️ Los pagos son **irreversibles**. Una vez enviada, una propuesta no puede editarse, solo eliminarse antes de ser aprobada.

---

## Seguridad

### Modelo multisig
Toda transacción requiere que múltiples miembros firmen con sus wallets individuales. Ninguna clave centralizada controla los fondos.

### Non-custodial
Trezu no custodia los activos. Los fondos permanecen bajo control del equipo en todo momento.

### Umbrales configurables
El equipo define cuántas firmas son necesarias para aprobar una propuesta (ej: 3 de 5 miembros Finance).

### Duración de votación configurable
Se puede establecer cuánto tiempo permanece abierta una votación antes de expirar.

### Mínimo privilegio
Los roles están diseñados para que nadie tenga más acceso del necesario. Governance no puede mover fondos; Finance no puede cambiar la configuración.

### Compatibilidad con hardware wallets
Soporte para **Ledger** como capa adicional de seguridad para firmantes críticos.

### Mejores prácticas recomendadas por Trezu
- Asignar Governance solo a wallets de hardware compartidas entre miembros de confianza
- Revisar membresías periódicamente
- Configurar umbrales de votación intencionalmente (no usar valores mínimos por defecto)
- Mantener separación de funciones: no asignar Requestor + Finance a los mismos miembros

---

## Blockchains soportadas

Trezu soporta **más de 30 redes**, incluyendo:

`Ethereum` · `NEAR` · `Solana` · `Bitcoin` · `Polygon` · `Sui` · `TON` · `Cardano` · `Avalanche` · `BNB Chain`

La gestión multi-chain permite mantener activos en distintas redes y operar desde una única interfaz, eliminando la necesidad de wallets separadas por blockchain.

---

## Address Book

Trezu incluye una **libreta de direcciones** donde se pueden guardar wallets frecuentes asociadas a múltiples blockchains. Reduce errores al evitar copiar/pegar direcciones manualmente en cada propuesta.

---

## Recursos

- Documentación oficial: https://docs.trezu.org
- Caso de uso ejemplo: [[Trezu - Caso de Uso DAO]]

---

## Tags

#cripto #tesorería #multisig #web3 #dao #non-custodial #trezu #seguridad #gobernanza
