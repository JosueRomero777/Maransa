# Maransa

## Diagrama de procesos — Comercialización, Logística y Empacado

![Diagrama de procesos](./diagrama_procesos.svg)

> Si el SVG no se renderiza en tu visor, abre `diagrama_procesos.html` o `diagrama_procesos.svg` en el navegador.

## Resumen
Este repositorio contiene un diagrama y la documentación inicial de los procesos de la empresa Maransa S.A.S relacionados con la comercialización, logística, control de calidad (laboratorio), custodia, empacado y exportación de camarón. El objetivo es disponer de una visión clara para diseñar un sistema de logística y facturación.

## Descripción detallada de los procesos

1. Comercialización / Inspección in situ
	- El equipo comercial visita la camaronera o cliente.
	- Realizan evaluación organoléptica: textura, color, olor, sabor.
	- Resultado: decidir si el lote puede comprarse/ser exportado o se rechaza.

# Maransa

## Diagrama de procesos — Comercialización, Logística y Empacado

![Diagrama de procesos](./diagrama_procesos.svg)

> Si el SVG no se renderiza en tu visor, abre `diagrama_procesos.html` o `diagrama_procesos.svg` en el navegador.

## Resumen
Este repositorio contiene un diagrama y la documentación inicial de los procesos de la empresa Maransa S.A.S relacionados con la comercialización, logística, control de calidad (laboratorio), custodia, empacado y exportación de camarón. El objetivo es disponer de una visión clara para diseñar un sistema de logística y facturación.

## Descripción detallada de los procesos

1. Comercialización / Inspección in situ
	- El equipo comercial visita la camaronera o cliente.
	- Realizan evaluación organoléptica: textura, color, olor, sabor.
	- Resultado: decidir si el lote puede comprarse/ser exportado o se rechaza.

2. Muestreo y análisis de laboratorio
	- Si la inspección inicial es favorable, se toma una muestra y se envía al laboratorio.
	- El laboratorio analiza parámetros sanitarios y de calidad.
	- Resultado: aprobado → seguir; rechazado → fin o reporte de incidencia.

3. Programación de volumen y coordinación logística
	- Se estiman las libras a movilizar y se coordina con logística (vehículos y tiempos).

4. Preparación de transporte
	- Logística asigna vehículos acondicionados (furgones, tanques, tanques de oxígeno si es camarón vivo).
	- Se designa conductor y se prepara la ruta.

5. Pesca / Cosecha
	- En caso de pesca contratada, la operación puede durar 6–7 horas.
	- Se confirma el volumen real después de la pesca.

6. Custodia
	- El personal de custodia (interno) recoge la pesca y la acompaña hasta el destino (ej.: provincia del Guayas, cantón Durán).
	- Registra incidencias en ruta si las hay.

7. Recepción en Empacadora
	- Apertura de furgones, verificación de cantidad, peso y condiciones.
	- Un inspector de la empresa controla el producto al llegar.

8. Análisis del laboratorio de la empacadora
	- La empacadora realiza su propio análisis; acepta o rechaza la carga.
	- Si acepta, la carga entra al proceso; si rechaza, se registra la incidencia y se decide devolución o tratamiento.

9. Clasificación y procesamiento
	- Según el tipo de camarón (cola, parentero, vivo) se asigna el proceso: empacado, congelado, preparación en máster.

10. Preparación para exportación y envío
	- Empacado final en máster, generación de documentación y envío a compradores o consolidadores.

11. Productos de producción propia (piscicultura)
	- Para camarón producido en piscinas propias, se sigue un flujo similar, pero la empresa asume la responsabilidad y calcula costos de producción antes de empacar/exportar.

## Departamentos y responsabilidades
- Comercialización / Compras: inspección, negociación y solicitudes de compra.
- Laboratorio: análisis de muestras (empresa y empacadora), emisión de certificados.
- Logística / Transporte: preparación de vehículos, programación de recolección y entregas.
- Custodia: acompañamiento, seguridad y trazabilidad en ruta.
- Empacadora / Procesamiento: recepción, control de calidad, empacado y congelado.
- Producción / Piscicultura: gestión de producción propia y cálculo de costos.
- Administración / Facturación: emisión de facturas, control de costos y documentación de exportación.

## Campos mínimos recomendados para el sistema (logística + facturación)
- Pedido / Lote: `id_pedido`, `fecha_solicitud`, `cliente`, `origen`, `tipo_camarao`, `estado`.
- Inspección Comercial: `id_inspeccion`, `inspector`, `fecha`, `textura`, `color`, `olor`, `observaciones`, `resultado`.
- Laboratorio: `id_muestra`, `id_pedido`, `fecha_muestra`, `analista`, `parametros`, `resultado`, `certificado`.
- Transporte: `id_transporte`, `vehiculo`, `equipo`, `conductor`, `fecha_recojo`, `ruta`, `costo`.
- Custodia: `id_custodia`, `agente`, `inicio`, `fin`, `incidencias`.
- Recepción / Empacadora: `id_recepcion`, `fecha`, `peso_libras`, `conteo_bultos`, `analisis_empacadora`, `resultado`.
- Procesamiento: `id_lote_procesado`, `tipo_procesamiento`, `temperatura`, `fecha_empacado`, `numero_master`, `destino`.
- Facturación: `id_factura`, `id_pedido`, `fecha_factura`, `items`, `total`, `estado_pago`.
- Incidencias y trazabilidad: `id_incidencia`, `relacionado_con`, `descripcion`, `evidencias`, `estado`, `resolucion`.

## Casos límite y consideraciones
- Camarón vivo: requiere tanques y oxígeno; tiempos cortos de transporte y mayor trazabilidad.
- Variación entre libras programadas y reales: debe contemplarse en facturación y logística.
- Rechazo en llegada a empacadora: definir política de devolución o compensación.
- Documentación sanitaria y certificados exigidos para exportación.

## Siguientes pasos recomendados (priorizados)
1. Modelar la base de datos con las tablas sugeridas y relaciones (Pedido, Muestras, Transporte, Recepciones, Facturas, Incidencias).
2. Prototipar API mínima: crear pedido → registrar inspección → programar transporte → registrar recepción → generar factura.
3. Implementar UI/UX básico para celular: formularios de inspección, app de conductor para registros y foto-evidencias.
4. Integrar generación/almacenamiento de certificados de laboratorio (PDF) y trazabilidad por lote.

## Archivos del repositorio
- `diagrama_procesos.svg` — diagrama vectorial (embed en README).
- `diagram.mmd` — diagrama en formato Mermaid (editable).
- `diagrama_procesos.html` — visor HTML que carga el SVG (útil si tu visor no renderiza SVG en README).

---

Si quieres que exporte el diagrama a PNG y lo añada al repo, dime resolución deseada y lo intento (puede requerir instalar una herramienta o usar un servicio externo). También puedo generar un `.drawio` editable.

Fecha: 2025-11-06
