
# Módulo III — Tesorería, Gestión Fiscal y Reportabilidad

**ERP Académico | Fundamentos de Sistemas de Información | UNSA | 2026-B**

## Descripción general

El presente repositorio contiene la documentación, el diseño y, posteriormente, la implementación del **Módulo III: Tesorería, Gestión Fiscal y Reportabilidad**, perteneciente al sistema ERP académico desarrollado en el curso de Fundamentos de Sistemas de Información de la Universidad Nacional de San Agustín de Arequipa.

El módulo tiene como finalidad apoyar la gestión financiera de una organización mediante el control de monedas y tipos de cambio, la configuración tributaria, el análisis del flujo de caja, los procesos de revaluación cambiaria y la generación de información financiera para la toma de decisiones.

Su desarrollo contempla la integración con los demás módulos del ERP, procurando mantener la consistencia de los datos, la trazabilidad de las operaciones y la separación de responsabilidades entre los equipos.

> **Estado del proyecto:** etapa de análisis y diseño. La arquitectura y el diccionario de datos constituyen propuestas técnicas sujetas a validación e integración con los demás equipos.

---

## 1. Objetivo general

Diseñar e implementar un módulo financiero integrado al ERP académico que permita administrar información de tesorería, configuración tributaria, diferencias cambiarias y reportabilidad financiera, garantizando la integridad, trazabilidad y disponibilidad de los datos.

### Objetivos específicos

- Diseñar la estructura de datos necesaria para gestionar monedas y tipos de cambio.
- Definir mecanismos de configuración de impuestos y sus relaciones contables.
- Proponer procesos para registrar movimientos de tesorería y analizar el flujo de caja.
- Establecer reglas para el cálculo y registro de diferencias cambiarias.
- Diseñar mecanismos de consulta y generación de reportes financieros.
- Definir la integración con los demás módulos del ERP.
- Documentar las reglas de negocio, relaciones y restricciones del sistema.
- Preparar una arquitectura modular que facilite el mantenimiento y la evolución del proyecto.

---

## 2. Alcance funcional

El Módulo III comprende cuatro áreas funcionales, de acuerdo con la propuesta de división del sistema financiero.

### 2.1. Gestión de monedas y tipos de cambio

Este componente administra las monedas utilizadas en las operaciones financieras y los tipos de cambio asociados a fechas determinadas.

**Funcionalidades previstas:**

- Registro y consulta de monedas.
- Gestión de tipos de cambio por fecha.
- Registro de valores de compra y venta.
- Identificación de la fuente de información cambiaria.
- Validación de valores y prevención de registros duplicados.

### 2.2. Gestión fiscal y tributaria

Este componente centraliza los parámetros tributarios necesarios para apoyar el tratamiento fiscal de las operaciones del ERP.

**Funcionalidades previstas:**

- Configuración de impuestos aplicables.
- Administración de tasas y períodos de vigencia.
- Asociación de impuestos con cuentas contables.
- Validación de parámetros tributarios.
- Consulta de configuraciones históricas.

Las tasas y reglas fiscales deberán contrastarse con la normativa vigente y las indicaciones del docente antes de implementarse.

### 2.3. Gestión cambiaria y flujo de caja

Este componente contempla el seguimiento de movimientos financieros y el tratamiento de operaciones expresadas en distintas monedas.

**Funcionalidades previstas:**

- Registro y consulta de movimientos de tesorería.
- Clasificación de entradas y salidas de dinero.
- Consolidación de información para el flujo de caja.
- Identificación de saldos sujetos a revaluación.
- Cálculo de diferencias cambiarias.
- Generación de resultados para su integración contable.

### 2.4. Reportabilidad financiera y cierre contable

Este componente está orientado a consultar información financiera consolidada y apoyar los procesos de cierre de períodos.

**Funcionalidades previstas:**

- Consulta de información contable consolidada.
- Preparación de reportes financieros.
- Apoyo a la generación del balance general y estado de resultados.
- Seguimiento de períodos contables.
- Consulta de resultados de cierres.
- Identificación de inconsistencias previas a la consolidación.

La responsabilidad definitiva sobre la ejecución de cierres y la generación de asientos contables deberá coordinarse con el equipo responsable del motor contable.

---

## 3. Arquitectura propuesta

Se plantea una **arquitectura modular en capas**, orientada a separar las responsabilidades de presentación, aplicación, dominio y persistencia.

| Capa | Responsabilidad |
|---|---|
| Presentación | Interfaces para registro, consulta y visualización de información financiera. |
| Aplicación | Coordinación de casos de uso y operaciones del módulo. |
| Dominio | Reglas de negocio, validaciones y cálculos financieros. |
| Persistencia | Almacenamiento y recuperación de información en PostgreSQL. |
| Integración | Intercambio controlado de información con otros módulos del ERP. |

### Principios de diseño

- **Modularidad:** separación de funcionalidades por responsabilidad.
- **Bajo acoplamiento:** reducción de dependencias directas entre módulos.
- **Integridad de datos:** utilización de restricciones y validaciones.
- **Trazabilidad:** identificación de operaciones y cambios relevantes.
- **Mantenibilidad:** organización del código y documentación.
- **Seguridad:** control de acceso y protección de operaciones sensibles.
- **Interoperabilidad:** definición de contratos para el intercambio de información.

### Integración con el ERP

Como estrategia inicial, se considera el mecanismo de **cierre y envío**, indicado para el trabajo académico.

Este enfoque permite que los módulos operativos consoliden su información antes de remitirla al componente contable correspondiente.

El Módulo III deberá consumir la información que necesite para sus reportes y remitir los resultados de sus procesos financieros cuando corresponda, sin modificar directamente las tablas definitivas administradas por otros equipos.

Los formatos de intercambio, responsables y reglas de validación serán definidos mediante coordinación entre equipos.

---

## 4. Tecnologías propuestas

| Tecnología | Uso previsto |
|---|---|
| PostgreSQL | Sistema gestor de base de datos relacional. |
| SQL | Definición de estructuras, consultas y restricciones. |
| Git | Control de versiones. |
| GitHub | Repositorio y colaboración del equipo. |
| REST API | Alternativa propuesta para la comunicación entre componentes. |
| Markdown | Documentación técnica del proyecto. |

**Nota:** el lenguaje y framework del backend y frontend aún deben definirse de acuerdo con las decisiones técnicas del equipo y los lineamientos generales del ERP.

---

## 5. Modelo y diccionario de datos

El diseño de la base de datos se desarrolla tomando como referencia la estructura documental utilizada por los equipos del ERP y la compatibilidad con PostgreSQL.

El diccionario de datos se organiza en siete secciones:

1. **Sistemas:** identificación y descripción del sistema ERP.
2. **Subsistemas:** clasificación de las áreas funcionales del módulo.
3. **Entidades:** definición de los objetos de información relevantes.
4. **Tablas de Datos:** descripción de atributos y estructuras operativas.
5. **Tablas Referenciales:** catálogos y valores controlados.
6. **Interrelaciones:** relaciones, dependencias y cardinalidades.
7. **Reglas:** restricciones y validaciones aplicables a los datos.

El diseño contempla la identificación de claves primarias, claves foráneas, tipos de datos, obligatoriedad de campos y reglas de integridad.

Las tablas compartidas deberán tener un responsable definido para evitar duplicaciones entre los módulos del ERP.

---

## 6. Estructura del repositorio

```text
fsi-2026b-modulo03-finanzas/
│
├── README.md
├── .gitignore
│
├── docs/
│   ├── arquitectura/
│   │   └── Propuesta_Arquitectura_Modulo_III.pdf
│   │
│   └── diccionario-datos/
│       ├── Diccionario_Datos_Modulo_III.xlsx
│       └── Diccionario_Datos_Modulo_III.pdf
│
├── backend/
│   └── .gitkeep
│
├── frontend/
│   └── .gitkeep
│
└── database/
    └── .gitkeep
```

### Descripción de directorios

| Directorio | Descripción |
|---|---|
| `docs/arquitectura/` | Propuesta arquitectónica y documentación de diseño. |
| `docs/diccionario-datos/` | Diccionario de datos en formatos Excel y PDF. |
| `backend/` | Espacio reservado para la implementación de servicios y lógica de negocio. |
| `frontend/` | Espacio reservado para las interfaces de usuario. |
| `database/` | Espacio reservado para scripts SQL, migraciones y otros recursos de base de datos. |

Las carpetas destinadas a implementación se mantienen preparadas para las siguientes etapas del proyecto.

---

## 7. Reglas de negocio principales

Se consideran inicialmente las siguientes reglas:

- Cada moneda deberá contar con un código único.
- Los tipos de cambio deberán ser positivos y estar asociados a una fecha y fuente.
- Las configuraciones tributarias deberán respetar sus períodos de vigencia.
- Los movimientos de tesorería deberán registrar importes válidos y una moneda asociada.
- Las operaciones de revaluación deberán utilizar información cambiaria identificable.
- Los resultados de los procesos financieros deberán conservar trazabilidad.
- La información utilizada en los reportes deberá provenir de fuentes autorizadas.
- Los procesos de cierre deberán respetar las restricciones del período contable.
- Los datos compartidos deberán mantenerse consistentes con los módulos responsables.

Las reglas definitivas se establecerán después de validar el diccionario de datos y los contratos de integración.

---

## 8. Seguridad e integridad

El diseño contempla las siguientes consideraciones:

- Validación de entradas en los servicios de aplicación.
- Restricciones de integridad referencial en PostgreSQL.
- Control de acceso según las responsabilidades de cada usuario.
- Protección de operaciones financieras sensibles.
- Registro de operaciones relevantes para auditoría.
- Uso de transacciones para operaciones que requieran consistencia.
- Manejo controlado de errores.
- Separación entre datos operativos y parámetros de configuración.

---

## 9. Equipo de trabajo

**Universidad:** Universidad Nacional de San Agustín de Arequipa  
**Curso:** Fundamentos de Sistemas de Información  
**Semestre:** 2026-B  
**Tribu:** 3 — Finanzas  
**Grupo:** C  
**Equipo:** 3  
**Módulo:** Tesorería, Gestión Fiscal y Reportabilidad

| Integrante | Rol |
|---|---|
| Subia Huaicane Edson Fabricio | Scrum Master |
| Dávila Flores Mathias Dario | Product Owner |
| Quispe Diaz Sara Sofia | Backend / Frontend |

La distribución de responsabilidades podrá actualizarse conforme avance el proyecto.

---

## 10. Estado y planificación del proyecto

| Etapa | Situación |
|---|---|
| Análisis del alcance | Propuesta inicial elaborada |
| Propuesta de arquitectura | Documento preparado para revisión |
| Diccionario de datos | Documento preparado para revisión |
| Organización del repositorio | Estructura inicial definida |
| Diseño físico de la base de datos | Pendiente de validación |
| Implementación del backend | Pendiente |
| Implementación del frontend | Pendiente |
| Integración con otros módulos | Pendiente |
| Pruebas funcionales | Pendiente |
| Despliegue | Pendiente |

### Próximas actividades

1. Validar el alcance funcional con el docente.
2. Coordinar las entidades compartidas con los otros equipos.
3. Revisar y aprobar el diccionario de datos.
4. Definir los contratos de integración.
5. Elaborar los scripts iniciales de PostgreSQL.
6. Seleccionar las tecnologías de implementación.
7. Implementar las funcionalidades por incrementos.
8. Incorporar pruebas y documentación técnica.

---

## 11. Documentación disponible

La documentación principal del módulo se organiza en:

- **Propuesta de Arquitectura:** componentes, responsabilidades, integración, seguridad y planificación técnica.
- **Diccionario de Datos:** entidades, atributos, tablas, interrelaciones y reglas del módulo.

Los documentos se encuentran en el directorio `docs/` del repositorio.

---

## 12. Consideraciones finales

El Módulo III forma parte de un ERP académico integrado y, por tanto, requiere coordinación permanente con los demás equipos.

La arquitectura y el modelo de datos se han planteado con énfasis en la separación de responsabilidades, la consistencia de la información financiera y la posibilidad de evolución incremental.

Este repositorio centraliza los avances del equipo y permitirá mantener la trazabilidad de las decisiones, la documentación y el desarrollo del módulo durante el curso.

---

**Universidad Nacional de San Agustín de Arequipa**  
**Fundamentos de Sistemas de Información — 2026-B**  
**Tribu Finanzas | Grupo C | Equipo 3**
