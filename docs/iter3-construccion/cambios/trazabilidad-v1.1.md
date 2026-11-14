# Trazabilidad v1.1

| RF | Requisito | HU | CU | Clases | Pruebas | Cambio |
|---|---|---|---|---|---|---|
| RF-01 | Registrar pedido | HU-01, HU-02 | CU-01 | CLS-01 Pedido, CLS-02 DetallePedido, CLS-04 Cliente | PR-01, PR-02 | Sin cambio |
| RF-02 | Validar disponibilidad | HU-03 | CU-02 | CLS-03 Producto, CLS-01 Pedido | PR-03, PR-04 | Sin cambio |
| RF-03 | Modificar o cancelar pedido | HU-04, HU-05 | CU-03 | CLS-01 Pedido | PR-05, PR-14 | Sin cambio |
| RF-04 | Preparar pedido y estados | HU-06, HU-07 | CU-04 | CLS-05 Comanda, CLS-01 Pedido | PR-06, PR-07 | Sin cambio |
| RF-05 | Gestionar faltante de insumos | HU-08 | CU-05 | CLS-10 Insumo, CLS-05 Comanda | PR-08, PR-15 | Sin cambio |
| RF-06 | Despachar y confirmar entrega | HU-09, HU-10 | CU-06 | CLS-06 Despacho, CLS-01 Pedido | PR-09, PR-16 | Sin cambio |
| RF-07 | Registrar y validar cobro (efectivo, tarjeta, billetera digital) | HU-11, HU-12 | CU-07 | CLS-07 Pago, CLS-01 Pedido | PR-10, PR-11, PR-22 | Modificado |
| RF-08 | Emitir comprobante (indica medio de pago) | HU-13 | CU-08 | CLS-08 Comprobante, CLS-07 Pago | PR-12, PR-17 | Modificado |
| RF-09 | Anular comprobante o reembolsar (por el medio original) | HU-14 | CU-09 | CLS-09 Reembolso, CLS-08 Comprobante, CLS-07 Pago | PR-13, PR-18, PR-23 | Modificado |
| RF-10 | Validar operación de pago digital | HU-15, HU-16 | CU-10 | CLS-11 ValidadorOperacion, CLS-07 Pago | PR-19, PR-20, PR-21 | Nuevo |

## Pruebas

| Prueba | RF | CU | Tipo | Descripción | Estado |
|---|---|---|---|---|---|
| PR-01 | RF-01 | CU-01 | Positiva | Registrar pedido con ítems válidos | Sin cambio |
| PR-02 | RF-01 | CU-01 | Negativa | Rechazar pedido sin ítems | Sin cambio |
| PR-03 | RF-02 | CU-02 | Positiva | Confirmar disponibilidad con stock suficiente | Sin cambio |
| PR-04 | RF-02 | CU-02 | Negativa | Sin stock: ofrecer alternativa del menú | Sin cambio |
| PR-05 | RF-03 | CU-03 | Positiva | Cancelar pedido antes del cobro | Sin cambio |
| PR-06 | RF-04 | CU-04 | Positiva | Avanzar estados Registrado, En preparación, Listo | Sin cambio |
| PR-07 | RF-04 | CU-04 | Negativa | Rechazar transición de estado inválida | Sin cambio |
| PR-08 | RF-05 | CU-05 | Positiva | Notificar faltante de insumo al cajero | Sin cambio |
| PR-09 | RF-06 | CU-06 | Positiva | Despachar y confirmar entrega de pedido Listo | Sin cambio |
| PR-10 | RF-07 | CU-07 | Positiva | Cobrar en efectivo o tarjeta (ahora registra el medio de pago) | Revisada |
| PR-11 | RF-07 | CU-07 | Negativa | Pago rechazado: máx. 2 reintentos y anulación | Revisada |
| PR-12 | RF-08 | CU-08 | Positiva | Emitir comprobante de pedido cobrado (muestra medio de pago) | Revisada |
| PR-13 | RF-09 | CU-09 | Positiva | Reembolso parcial por ítem anulado (por el medio original) | Revisada |
| PR-14 | RF-03 | CU-03 | Negativa | Rechazar cancelación de pedido ya despachado | Nueva |
| PR-15 | RF-05 | CU-05 | Negativa | Faltante en todos los ítems anula el pedido completo | Nueva |
| PR-16 | RF-06 | CU-06 | Negativa | Rechazar despacho de pedido que no está Listo | Nueva |
| PR-17 | RF-08 | CU-08 | Negativa | No emitir comprobante si el pago no está validado | Nueva |
| PR-18 | RF-09 | CU-09 | Negativa | Rechazar reembolso mayor al monto cobrado | Nueva |
| PR-19 | RF-10 | CU-10 | Positiva | Validar operación digital con código correcto | Nueva |
| PR-20 | RF-10 | CU-10 | Negativa | Rechazar código de operación duplicado | Nueva |
| PR-21 | RF-10 | CU-10 | Negativa | Rechazar código con formato inválido | Nueva |
| PR-22 | RF-07 | CU-07 | Positiva | Cobrar con billetera digital (Yape o Plin) | Nueva |
| PR-23 | RF-09 | CU-09 | Positiva | Reembolsar por el mismo medio digital | Nueva |

## Cobertura

Pruebas: 13 (v1.0) y 23 (v1.1). RF con prueba positiva y negativa: 4 de 9 (v1.0) y 10 de 10 (v1.1).
