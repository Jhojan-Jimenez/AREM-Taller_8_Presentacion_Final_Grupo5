# Reflexión Individual

## Nombre del Estudiante
**Carlos David Bello Ortiz**

## Rol en el equipo
Responsable del análisis de seguridad y cumplimiento normativo. Lideré el desarrollo del análisis STRIDE del taller 5, construyendo la tabla de amenazas sobre cada componente de la arquitectura de A&C Ingeniería, y coordiné la investigación del taller 6 sobre el marco normativo colombiano aplicable al cliente. Además, participé en la estructuración de las referencias bibliográficas y en la revisión de coherencia entre los entregables del corte.

---

## Aprendizajes Clave

- Aprendí a aplicar el modelo STRIDE no como un ejercicio teórico de clasificación, sino como una herramienta de pensamiento adversarial: la pregunta no es "¿a qué categoría pertenece esta amenaza?" sino "¿cómo atacaría yo este sistema si quisiera hacerle daño al negocio?". Esa perspectiva cambia completamente la manera de aproximarse al análisis de seguridad.

- Comprendí que la seguridad y el cumplimiento normativo no son capas independientes que se agregan al final de un proyecto tecnológico: emergen directamente de la arquitectura. En A&C, el mayor riesgo de seguridad —la falta de trazabilidad entre sistemas— no es un problema de configuración del ERP sino una consecuencia de la arquitectura de integración. No se puede "parchear" con una herramienta de seguridad; requiere cambios arquitectónicos.

- Practiqué habilidades de investigación normativa aplicada. Antes del curso, normas como la Ley 1581 de 2012 o ISO/IEC 27001 me parecían documentos abstractos. Usarlas para evaluar la realidad concreta de una empresa me enseñó a leerlas de otra manera: no como listas de obligaciones, sino como mapas de riesgo organizacional.

---

## Retos Superados

- El mayor reto fue establecer supuestos razonables para el análisis STRIDE en áreas donde no teníamos información explícita del cliente. Por ejemplo, no sabíamos con exactitud qué mecanismos de backup usaba la empresa. Opté por asumir el escenario más conservador (sin backup formalizado) y documentarlo explícitamente como supuesto, en lugar de inventar una capacidad que no podíamos verificar. Esa disciplina de ser transparente sobre los supuestos fue algo que el docente valoró en la retroalimentación.

- Al principio confundí el nivel de detalle apropiado para el análisis de amenazas: quería documentar absolutamente todas las posibles amenazas sobre cada subcomponente, lo que generó un análisis tan granular que perdía la visión de conjunto. Aprendí a priorizar por impacto en el negocio: las amenazas que paralizan operaciones críticas primero, las que afectan procesos secundarios después.

---

## Áreas por Mejorar

- Me gustaría profundizar en los aspectos prácticos de la implementación de ISO/IEC 27001: el análisis del taller 6 identificó las brechas, pero me quedé con la inquietud de cómo se concreta un SGSI en una empresa del tamaño de A&C con recursos limitados. Esa brecha entre el diagnóstico y la implementación es algo que quiero explorar.

- Reconozco que debo mejorar mis habilidades de presentación oral. Durante la simulación del comité de arquitectura, me costó sintetizar el análisis STRIDE en menos de dos minutos de manera clara para una audiencia no técnica. El análisis estaba sólido, pero la comunicación del riesgo a nivel ejecutivo requiere un lenguaje diferente al del informe técnico.

---

## Contribución Personal

Siento que mi mayor aporte al equipo fue aportar la perspectiva del "¿qué puede salir mal?". En un proyecto arquitectónico es fácil enamorarse de la solución propuesta y de los diagramas bien hechos. Mi rol de analista de seguridad me obligaba constantemente a preguntar: ¿qué pasa si el servidor cae? ¿qué pasa si alguien con permisos excesivos exporta la base de clientes? ¿qué consecuencia legal tendría ese evento para el cliente? Esa tensión, aunque incómoda a veces dentro del equipo, hizo que la arquitectura propuesta fuera más honesta y más robusta.

---

_Esta reflexión individual hace parte de la entrega final del curso AREM — Arquitectura Empresarial — Universidad de La Sabana._