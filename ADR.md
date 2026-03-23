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
