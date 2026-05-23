# Resumen Ejecutivo del Proyecto Arquitectónico

## Nombre del Cliente
**Automatización y Control Ingeniería S.A.S — A&C Ingeniería**  
Contacto: Sebastián Salgado (Gerente) · Bogotá, Carrera 12 No. 18-20 · Tel: 3113519535

---

## Objetivo General del Proyecto

A lo largo del curso de Arquitectura Empresarial, el Grupo 5 realizó un análisis arquitectónico completo de **A&C Ingeniería S.A.S**, empresa del sector industrial dedicada a la comercialización de componentes electrónicos, la fabricación de sensores de temperatura y nivel bajo la marca **SENSA**, y el diseño y puesta en marcha de proyectos de automatización industrial.

El reto central identificado desde la caracterización inicial fue la **ausencia de integración entre los sistemas tecnológicos de la empresa**: el ERP on-premise, el CRM Zoho One en la nube y Google Drive/OneDrive operan como islas independientes, obligando al equipo comercial a realizar tareas repetitivas y manuales (búsqueda en catálogo PDF, cálculo manual de precios, transcripción de datos entre sistemas) que ralentizan el tiempo de respuesta al cliente y aumentan la probabilidad de errores.

El valor aportado por el análisis fue construir una visión arquitectónica estructurada y multicapa que evidencia dónde están las brechas, qué riesgos representan para el negocio, y qué camino de mejora es coherente con las restricciones reales del cliente (mantener el ERP y el CRM actuales, minimizar cambios disruptivos, solución escalable a futuro).

---

## Vistas Arquitectónicas Cubiertas

| Vista                    | Alcance de la solución desarrollada                                                                                   |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------|
| **Procesos de Negocio**  | Modelado BPMN del proceso de comercialización (recepción de solicitud → lead CRM → cotización → cierre de venta → despacho), gestión administrativa e integración y proyectos (FAT/SAT) |
| **Información / Datos**  | Modelo entidad-relación con siete entidades clave: Cliente, Producto, Cotización, Detalle Cotización, Venta, Factura y Despacho; identificación de silos de datos entre ERP, CRM y Drive |
| **Aplicaciones / Sistemas** | Mapa de aplicaciones: CRM Zoho One, ERP World Office, MS Word/Excel, Google Drive/OneDrive, Catálogo PDF; diagrama de contexto e identificación del gap de integración entre sistemas |
| **Infraestructura**      | Mapa de infraestructura física: servidor on-premise único con BD del ERP + Google Drive en nube pública sin comunicación automatizada; diagnóstico de punto único de falla, falta de HA y ausencia de integración entre entornos |
| **Seguridad**            | Análisis STRIDE sobre todos los activos críticos (ERP, BD, Drive, servidor, red, flujos manuales); tabla de amenazas con probabilidad, impacto, controles existentes y mitigaciones recomendadas |
| **Cumplimiento Normativo** | Checklist de cumplimiento frente a Ley 1581 de 2012 (Habeas Data), ISO/IEC 27001 y normativa DIAN; matriz de brechas y plan de acción priorizado por impacto en seguridad, continuidad y cumplimiento legal |

---

## Hallazgos Clave

- **Gap de integración crítico:** El ERP y Google Drive no tienen comunicación automatizada. Todo el intercambio de información ocurre manualmente, generando silos de datos, duplicidades y riesgo de inconsistencias. El propio cliente confirmó: *"No se comunica el ERP con Google Drive"*.

- **Punto único de falla en infraestructura:** La empresa opera sobre un único servidor físico on-premise sin mecanismos de alta disponibilidad, backup automatizado ni plan formal de continuidad del negocio. Una falla de hardware detiene completamente la operación del ERP.

- **Proceso comercial con carga manual excesiva:** El asesor comercial debe cruzar cuatro sistemas de forma manual (CRM → catálogo PDF → Word/Excel → CRM) para generar una cotización. Esto incrementa el tiempo de respuesta y el riesgo de errores en precios, márgenes e IVA.

- **Controles de seguridad básicos sin formalización:** Los controles existentes (autenticación simple, roles generales en el ERP) no están documentados ni auditados. No existe monitoreo centralizado, gestión formal de incidentes ni política documentada de protección de datos.

- **Cumplimiento normativo parcial:** La empresa cumple con los principios básicos de la Ley 1581 de 2012 en la recolección de datos, pero no tiene políticas formalizadas, registros ante la SIC, ni procedimientos documentados de respuesta a incidentes de seguridad.

---

## Recomendaciones Principales

1. **Implementar una capa de integración (middleware/API)** entre el CRM Zoho One, el ERP World Office y Google Drive para eliminar el intercambio manual de información. Zoho Flow es una opción nativa compatible con el ecosistema Zoho existente.

2. **Digitalizar el catálogo de productos** e integrarlo directamente al CRM, permitiendo que los asesores busquen productos y obtengan precios con márgenes e IVA calculados automáticamente dentro del mismo flujo de cotización.

3. **Implementar backup automatizado y un plan básico de continuidad** sobre el servidor actual: copias de seguridad incrementales diarias hacia la nube, UPS y un procedimiento documentado de recuperación ante fallas de hardware.

4. **Formalizar la política de seguridad de la información** con base en ISO/IEC 27001: definir roles y responsabilidades, implementar autenticación multifactor (MFA) para acceso al ERP y al CRM, y establecer un registro centralizado de actividades (logs de auditoría).

5. **Registrar las bases de datos ante la SIC** (Registro Nacional de Bases de Datos — RNBD) y documentar las políticas de tratamiento de datos personales para cumplir plenamente con la Ley 1581 de 2012.

6. **Migrar el catálogo PDF a una base de datos estructurada** (puede ser dentro del ERP o una base de datos compartida accesible desde el CRM) para eliminar la búsqueda manual y garantizar que precios y disponibilidad sean siempre consistentes.

---

## Matriz de Riesgos Arquitectónicos

| Riesgo identificado                          | Probabilidad | Impacto   | Nivel de riesgo | Mitigación recomendada                           |
|----------------------------------------------|--------------|-----------|-----------------|--------------------------------------------------|
| Caída del servidor único (pérdida del ERP)   | Media        | Crítico   | **Crítico**     | Backup automático, UPS, plan de recuperación     |
| Error en cálculo manual de precios/márgenes  | Alta         | Alto      | **Alto**        | Integrar catálogo al CRM con cálculo automático  |
| Fuga de información en Google Drive          | Media        | Alto      | **Alto**        | Permisos por rol, DLP, políticas documentadas    |
| Versiones inconsistentes de datos (silos)    | Alta         | Medio     | **Alto**        | Capa de integración ERP ↔ CRM ↔ Drive           |
| Acceso no autorizado al ERP                  | Baja-Media   | Alto      | **Medio-Alto**  | MFA, principio de mínimo privilegio              |
| Incumplimiento Ley 1581 / RNBD               | Media        | Medio     | **Medio**       | Registro SIC, política de datos documentada      |
| Pérdida de cotizaciones sin trazabilidad     | Media        | Medio     | **Medio**       | Logs de auditoría en CRM, estados formalizados   |
| Dependencia de internet para CRM (SaaS)      | Baja         | Medio     | **Bajo-Medio**  | Plan de contingencia offline para casos críticos |

---

## Reflexión Final

Este ejercicio de análisis arquitectónico de A&C Ingeniería permitió al equipo materializar, sobre un caso real, cómo las cinco capas de la arquitectura empresarial se influyen mutuamente: un proceso de negocio ineficiente (comercialización manual) tiene su raíz en una vista de información fragmentada (silos entre ERP, CRM y Drive), que a su vez es consecuencia directa de una infraestructura mínima sin integración, y que se agrava por la ausencia de controles de seguridad formalizados que den gobernanza al flujo de datos entre sistemas.

La experiencia demostró que la arquitectura empresarial no es un conjunto de diagramas aislados, sino una narrativa coherente donde cada decisión técnica se puede rastrear hasta un objetivo estratégico del cliente. Para A&C, cuya visión es ser el proveedor preferido de ingeniería industrial a nivel nacional para 2026, la integración de sus sistemas no es una mejora estética: es el habilitador tecnológico sin el cual ese crecimiento no es sostenible.

---

_Este resumen ejecutivo forma parte de la entrega final del curso AREM — Arquitectura Empresarial — Universidad de La Sabana. Equipo Grupo 5, mayo de 2026._
