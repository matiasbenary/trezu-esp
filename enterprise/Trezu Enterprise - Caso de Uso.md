# Trezu — Caso de Uso Enterprise: Empresa de pagos internacionales en cripto

## Contexto

**RemitGlobal S.A.** es una empresa de servicios financieros con operaciones en 6 países que utiliza activos digitales para procesar pagos internacionales a proveedores y empleados remotos. Gestiona un volumen mensual de aproximadamente $800,000 USD en transferencias cripto (USDC, ETH, NEAR).

### Situación previa
El equipo financiero operaba con una wallet multisig básica. Los problemas detectados en una auditoría interna:

- Sin separación entre quien solicita y quien autoriza pagos
- Sin registro formal de justificaciones por transacción
- Dependencia operativa de 2 personas para aprobar cualquier movimiento
- Imposibilidad de delegar sin otorgar acceso total
- Sin protocolo para incorporar o desvincular firmantes

---

## Estructura implementada en Trezu

### Equipo y roles asignados

| Miembro | Área | Rol en Trezu |
|---|---|---|
| Directora Financiera | CFO | Governance + Finance |
| Controller | Contabilidad | Finance |
| Tesorero | Finanzas | Finance |
| Analista de Pagos 1 | Operaciones | Requestor |
| Analista de Pagos 2 | Operaciones | Requestor |
| Responsable RRHH | Recursos Humanos | Requestor |

### Configuración de controles

- **Umbral de aprobación**: 2 de 3 miembros Finance para pagos hasta $50,000 USD / 3 de 3 para montos superiores
- **Plazo de votación**: 24 horas para pagos operativos, 72 horas para operaciones extraordinarias
- **Governance**: custodiado en dispositivos Ledger, uso restringido a cambios de configuración auditados

---

## Escenario 1: Pago quincenal a empleados remotos

### Situación
La responsable de RRHH debe procesar los pagos quincenales a 15 empleados remotos en USDC sobre la red NEAR, por un total de $45,000.

### Flujo

```
Responsable RRHH (Requestor)
  └── Genera solicitud de pago múltiple
        ├── 15 destinatarios con montos individuales aprobados en nómina
        └── Adjunta referencia: "Nómina Q2 - período 01/05 al 15/05"

Controller (Finance)
  └── Verifica montos contra nómina aprobada por dirección
        └── Autoriza ✅

Tesorero (Finance)
  └── Confirma disponibilidad de fondos y valida cuentas de destino
        └── Autoriza ✅ → umbral alcanzado (2/3)

Trezu
  └── Ejecuta los 15 pagos automáticamente on-chain ✅
```

**Resultado:** Los pagos se procesan con trazabilidad completa. Cada empleado recibe su transferencia con registro de quién solicitó, quién autorizó y cuándo se ejecutó.

---

## Escenario 2: Pago a proveedor internacional de alto valor

### Situación
Un analista de pagos debe abonar una factura de $120,000 USD a un proveedor de tecnología con sede en Singapur, en ETH.

### Flujo

```
Analista de Pagos 1 (Requestor)
  └── Genera solicitud: $120,000 ETH → wallet proveedor
        └── Referencia: "Factura #SG-2025-0089 - Servicios tecnológicos Q2"

Sistema
  └── Detecta monto > $50,000 → requiere 3/3 Finance

Directora Financiera (Finance)
  └── Verifica contrato y factura
        └── Autoriza ✅

Controller (Finance)
  └── Confirma imputación contable
        └── Autoriza ✅

Tesorero (Finance)
  └── Valida fondos disponibles y tipo de cambio aplicado
        └── Autoriza ✅ → umbral alcanzado (3/3)

Trezu
  └── Ejecuta el pago ✅
```

**Resultado:** El control adicional en operaciones de alto valor reduce el riesgo operativo y satisface los requerimientos de autorización establecidos en la política financiera de la empresa.

---

## Escenario 3: Rebalanceo de tesorería entre redes

### Situación
La tesorería tiene exceso de liquidez en ETH y necesita USDC en NEAR para cubrir los pagos del mes siguiente.

### Flujo

```
Analista de Pagos 2 (Requestor)
  └── Genera solicitud de swap: 30 ETH → USDC en NEAR
        └── Referencia: "Rebalanceo tesorería - cobertura nómina junio"

Controller + Tesorero (Finance)
  └── Aprueban la operación (2/3, plazo estándar 24h)

Trezu
  └── Ejecuta el swap cross-chain directamente desde la tesorería ✅
```

---

## Escenario 4: Desvinculación de firmante

### Situación
El Controller deja la empresa. Es necesario revocar su acceso de forma inmediata y documentada.

### Flujo

```
Directora Financiera (Governance)
  └── Genera propuesta de configuración: remover al Controller del rol Finance

Tesorero (Governance)
  └── Autoriza el cambio de configuración

Trezu
  └── Revoca el acceso del Controller ✅
        └── El umbral se ajusta automáticamente: ahora requiere 2/2 Finance restantes
              └── Se registra el cambio con fecha y firmantes ✅
```

> La desvinculación queda auditada. El ex-miembro no puede ejecutar ni acceder a ninguna operación posterior.

---

## Resultados obtenidos

| Indicador | Antes | Con Trezu |
|---|---|---|
| Tiempo promedio de procesamiento de pago | 3-4 días | 6-24 horas |
| Transacciones con justificación documentada | ~30% | 100% |
| Operaciones auditables on-chain | 0% | 100% |
| Personas con acceso total a fondos | 2 | 0 |
| Tiempo de desvinculación de firmante | Días (manual) | Horas (proceso formal) |
| Incidentes por error de dirección | 3 en 12 meses | 0 (Address Book) |

---

## Configuración recomendada para empresas similares

```
Tesorería RemitGlobal
├── Governance: CFO + 1 Director, solo en hardware wallets (Ledger)
├── Finance: 3-5 miembros del área financiera
│     ├── Umbral estándar: 2/N para operaciones < $50,000
│     └── Umbral reforzado: N/N para operaciones > $50,000
├── Requestors: analistas operativos y áreas solicitantes (RRHH, Compras)
├── Plazo de votación: 24h operativo / 72h extraordinario
└── Address Book: todos los proveedores y cuentas recurrentes pre-validadas
```

---

## Tags

#trezu #enterprise #tesorería #pagos-internacionales #control-interno #activos-digitales #multisig #auditoría
