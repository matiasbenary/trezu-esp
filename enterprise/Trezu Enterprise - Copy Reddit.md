# Trezu — Copy Reddit Enterprise

---

## Post 1 — Control interno

**Título:** Cómo implementamos segregación de funciones en nuestra tesorería de activos digitales

---

Una de las primeras observaciones que recibimos en nuestra auditoría interna fue que los pagos en criptomonedas no tenían los mismos controles que los pagos bancarios tradicionales.

El problema era estructural: teníamos una wallet multisig donde las mismas personas que solicitaban un pago también podían aprobarlo. Sin segregación de funciones, sin justificación por transacción, sin registro formal de autorizaciones.

Implementamos **Trezu**, una plataforma de gestión de tesorería en activos digitales que separa los roles operativos por diseño:

- **Quienes solicitan pagos** no pueden aprobarlos
- **Quienes autorizan** no pueden modificar la configuración del sistema
- **Quienes administran el acceso** no pueden ejecutar operaciones financieras

Cada transacción requiere documentación de respaldo, pasa por un proceso de aprobación con umbral configurable y queda registrada on-chain con fecha, firmantes y referencia.

Para nosotros fue el paso necesario para poder reportar los movimientos en cripto con el mismo nivel de trazabilidad que exigimos en el resto de las operaciones financieras.

Soporta más de 30 redes (Ethereum, NEAR, Solana, Bitcoin, entre otras). Compatible con Ledger para los roles de mayor responsabilidad.

👉 https://docs.trezu.org

---

## Post 2 — Operaciones

**Título:** Le dimos estructura a nuestra tesorería cripto antes de que se convirtiera en un problema de gobierno

---

Cuando éramos 3 personas, manejar los fondos del proyecto en una wallet compartida era razonable.

Cuando llegamos a 15 personas operando en 4 países, ya no lo era.

El punto de quiebre fue cuando un empleado que se fue de la empresa todavía tenía acceso técnico a firmar transacciones. No había un proceso formal para revocar permisos, y tampoco había registro de qué había aprobado mientras estuvo.

Migramos a **Trezu** para darle estructura a la tesorería:

- Roles separados entre quienes proponen pagos y quienes los autorizan
- Proceso de incorporación y desvinculación de firmantes con registro
- Umbrales de aprobación diferenciados según el monto de la operación
- Auditoría completa de cada transacción: quién pidió, quién aprobó, cuándo ejecutó

No es una herramienta solo para DAOs. Es una solución para cualquier organización que necesite que su tesorería en cripto funcione con los mismos controles que esperan de cualquier área financiera.

👉 https://docs.trezu.org

---

## Post 3 — Pagos corporativos

**Título:** Procesamos $800K mensuales en cripto con aprobación formal y trazabilidad completa — así lo estructuramos

---

Operamos pagos internacionales en criptomonedas a proveedores y equipos distribuidos. Durante un tiempo lo hicimos con herramientas que no estaban pensadas para este nivel de operación.

Los problemas que terminamos resolviendo con **Trezu**:

**Segregación de funciones**
Los analistas que generan órdenes de pago no pueden aprobarlas. Las aprobaciones requieren al menos 2 de 3 miembros del equipo financiero para montos estándar, y unanimidad para operaciones de alto valor.

**Gestión de accesos**
Cuando alguien deja el equipo, su acceso se revoca a través de un proceso formal con registro. No hay claves compartidas ni accesos residuales.

**Trazabilidad**
Cada transacción tiene una referencia, un historial de aprobaciones y una marca de tiempo inmutable on-chain. Exportable para conciliación contable.

**Multi-chain desde una sola interfaz**
Operamos en NEAR, Ethereum y USDC sin necesidad de gestionar wallets separadas por red.

El resultado: cero incidentes por error de dirección desde que implementamos la libreta de cuentas, y tiempo de procesamiento reducido de 3-4 días a menos de 24 horas.

👉 https://docs.trezu.org

---

## Post 4 — Confidencialidad financiera

**Título:** Cómo implementamos pagos cripto confidenciales sin sacrificar controles internos

---

Existe un requerimiento que escucho con frecuencia en equipos financieros que operan con activos digitales: necesitan gestión de tesorería multisig, pero no pueden —o no quieren— que su información financiera sea pública.

Los casos más frecuentes que encontramos:
- Pagos a auditores de seguridad antes de que el informe esté publicado
- Contratos estratégicos donde exponer el monto podría afectar las negociaciones
- Nómina y pagos a proveedores que, por política interna, no se divulgan públicamente

La respuesta estándar en cripto —"todo es público en la blockchain"— no es aceptable para una organización que tiene estándares de confidencialidad financiera.

**Trezu** incorpora una modalidad de **Tesorería Confidencial** que resuelve esto. Los balances, el contenido de las propuestas y el historial de pagos son visibles únicamente para los miembros autorizados del equipo. Nada se expone en la blockchain pública.

La tecnología subyacente son los shards privados de NEAR Protocol: misma infraestructura que las tesorerías públicas, pero con privacidad financiera total. Los controles internos se mantienen intactos: separación de funciones, umbrales de aprobación configurables, trazabilidad interna y soporte para hardware wallets.

Lo que sigue siendo público por diseño: la lista de miembros y el resultado de cada votación. Lo que queda privado: balances, montos, destinatarios e historial de transacciones.

Para organizaciones que necesitan operar con privacidad financiera sin renunciar a los controles que exigen sus políticas internas, esta es la alternativa.

👉 https://docs.trezu.org
