# ADR EducaMás
**Fecha:** 23 de marzo de 2026

**Integrantes:** Darién Urrutia y Benjamin Larrondo

## Contexto:

La plataforma de cursos online "EducaMás" requiere definir cómo almacenar y entregar videos a estudiantes e instructores.

Por lo cual, El equipo de desarrollo está debatiendo sobre la estrategia de almacenamiento de los videos de los cursos:

* Opción A: Almacenamiento en la nube con CDN (Red de Entrega de Contenido):
Utilizar un servicio de almacenamiento en la nube como AWS S3 o Google Cloud
Storage, combinado con una CDN para la entrega eficiente de los videos a los usuarios.

* Opción B: Almacenamiento en servidores propios: Mantener los videos en servidores propios de la empresa.


### Factores relevantes:

**Factores relevantes para la decisión:**

* **Volumen estimado de videos:** Se proyectan 500 horas de video en el primer año .
* **Tráfico esperado:** Se estiman 10,000 usuarios concurrentes en horas pico .
* **Presupuesto:** Contamos con un presupuesto limitado para inversión inicial en infraestructura .
* **Requisitos de rendimiento:** Es fundamental asegurar una baja latencia en la reproducción .
* **Requisitos de seguridad:** Debemos proteger el contenido contra descargas no autorizadas .
* **Conocimientos técnicos:** El equipo tiene experiencia en servidores físicos, pero es nuevo en el uso de CDNs .

### Decisión:
Hemos decidido adoptar la Opción A: Almacenamiento en la nube con CDN.

**Justificación:** Dada la alta concurrencia de 10,000 usuarios, la infraestructura propia (Opción B) requeriría una inversión masiva en ancho de banda y hardware que excede el presupuesto limitado. La Opción A permite escalar según la demanda y garantiza la baja latencia necesaria mediante la CDN.

**Pros y Contras:**
* **Pros:** Alta disponibilidad, reducción de carga en el servidor principal, seguridad integrada (firmado de URLs) y mantenimiento delegado al proveedor.
* **Contras:** Curva de aprendizaje para el equipo en gestión de CDNs y dependencia directa de un proveedor externo (Vendor Lock-in).

### Consecuencias:
* **Impacto en el desarrollo:** El equipo debe aprender a utilizar SDKs para la subida de videos a S3/Cloud Storage y configurar la generación de URLs firmadas para la seguridad de los videos.
* **Impacto en el mantenimiento:** Se elimina la necesidad de gestionar hardware físico, parches de SO de servidores de almacenamiento y monitoreo de red local.
* **Impacto en los costos:** Los costos operativos (OpEx) variarán mensualmente según el tráfico y almacenamiento consumido.
* **Riesgos:** Si los costos de transferencia de datos de la CDN aumentan drásticamente por un éxito inesperado, el presupuesto podría verse presionado a largo plazo.

### Estado:
**Aceptado**
