
---
# Ingeniería del Software

[HOME](../../README.md)

---

##  T1 - Introducción a la Ingeniería del Software

- Los proyectos de software son difíciles:
	- Suelen costar más y tardar más tiempo de lo previsto.
	- Los costes se concentran en la ingeniería no en la producción.
	- Para evitarlo se aplican principios de ingeniería (del software)
- La ingeniería del software es la aplicación de un enfoque sistemático, disciplinado y cuantificable para el desarrollo, operación y mantenimiento del software.
- Sirve para solucionar problemas de usuarios
	- Para ello es necesario entender el problema y comunicarse de forma efectiva con él.
---
##  T2 - Procesos de software
Conjunto de actividades/productos obtenidos durante desarrollo de cualquier sistema de software:
1. **Análisis**. ¿Qué hacer?
2. **Diseño**. ¿Cómo hacerlo?
3. **Codificación**. Hacerlo
4. **Prueba**. ¿Es correcto
5. **Mantenimiento**. Mejorar, adaptar y corregir.

---
## T2 - Métrica v3
Es una metodología desarrollada por el Gobierno de España.
Está estructurada en varios procesos donde cada proceso tiene actividades y cada actividad tareas.
1. **PLANIFICACIÓN**
	1. **Planificación de Sistemas de Información (Proceso PSI)**
		1. Obtiene marco de referencia para el desarrollo
2. **DESARROLLO**
	1. [Estudio de la Viabilidad del Sistema (Proceso EVS)](data/EVS.md)
		1. Analiza necesidades del cliente y da solución a corto plazo definiendo proyecto.
	2. [**Análisis del Sistema de Información (Proceso ASI)**](data/ASI.md)
		1. Analiza la consistencia y especifica los requisitos.
	3. **Diseño del Sistema de Información (Proceso DSI)**
		1. Definir arquitectura del sistema y entorno tecnológico.
		2. Especificación detallada de componentes del sistema de información.
	4. **Construcción del Sistema de Información (Proceso CSI)**
		1. Desarrollo de procedimientos de operación y seguridad.
		2. Elaboración de manuales del usuario final.
	5. **Implantación y Aceptación del Sistema  (Proceso IAS)**
		1. Entrega y aceptación del sistema en su totalidad.
		2. Actividades necesarias para paso a producción.
3. **MANTENIMIENTO**
	1. **Mantenimiento del Sistema de Información (MSI)**

---
## T3 - Proceso de diseño (Proceso DSI)
- **Arquitectura (hardware y software)**
	- Se buscan nodos involucrados (hardware)
	- Se tiene en cuenta:
		- Infraestructura (propia o alojamiento externo)
		- Tecnología (software)
		- Eficiencia y seguridad
	- Diagramas 
		- de componentes (nodos)
		- de despliegue (nodos + artefactos)
		- de interacción (detalle de un escenario)
- **Diseño de datos (Base de datos)**
	- 1 clase = 1 tabla ; 1 atributo = 1 columna
	- Se escoge la clave principal
	- Se añaden relaciones y herencias
- **Plan de pruebas**
	- 1 - Se planean pruebas (plan temporal y pruebas de aceptación)
	- 2 - Se diseñan las pruebas (tipos, estrategia e integración)
	- 3 - Se ejecutan las pruebas
	- 4 - Se corrigen defectos (depuración)
---
## T4 - Pruebas: conceptos y proceso
- Definición de prueba
	- Proceso de ejecutar un programa con la intención de encontrar fallos
	- Buen caso de prueba = Probabilidad alta de encontrar nuevo fallo.
	- Caso de prueba con éxito = Detectar un fallo nuevo.
- Conceptos
	- **Error**. Acción humana que produce un resultado incorrecto
	- **Fallo**. Diferencia entre comportamiento esperado y observado del software.
	- **Defecto**. Desperfecto en un componente/sistema.
- Proceso
	- Especificación y diseño
		- Emplea técnicas de prueba
			- Técnicas basadas en condiciones (decisiones lógicas)
				- Cobertura de sentencias (Toda la decisión)
				- Cobertura de condiciones (partes sin operadores lógicos como AND y OR)
				- Cobertura de condición/decisión (Se prueban las partes y el conjunto)
				- Cobertura de múltiple condición (Todas, crecimiento exponencial)
			- Es necesario identificar situaciones de prueba (definir entorno de prueba)
		- Identifica de casos de prueba
		- Obtención de un Test Suite (conjunto de casos de prueba)
	- Ejecución. Software bajo prueba
	- Evaluación e informe (reporting)
		- Presentación de fallos descubiertos
	- Detección y corrección de pruebas (depuración)
---
## Extra - Tipos de diagramas
- **ASI**
	- Modelado funcional
		- Diagrama de casos de uso
	- Modelado de dominio
		- Diagrama de clases
		- Diagrama de transición de estados
		- Diagrama de actividad
- **DSI**
	- Diagrama de despliegue
	- Modelo Entidad/relación