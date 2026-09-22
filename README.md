# Virtualization Lab — Spring Boot, Docker, Docker Hub y AWS EC2

Proyecto desarrollado para el laboratorio de virtualización y despliegue de aplicaciones.

El proyecto demuestra el proceso completo de:

- Desarrollo de una aplicación web con Spring Boot.
- Construcción y ejecución local.
- Contenerización mediante Docker.
- Ejecución mediante Docker Compose.
- Publicación de una imagen en Docker Hub.
- Despliegue de la aplicación en una instancia AWS EC2.
- Configuración de seguridad mediante AWS Security Groups.
- Análisis básico del modelo de despliegue y costos de infraestructura.

---

## 1. Arquitectura general

La arquitectura implementada es la siguiente:

```text
                         CLIENTE
                            |
                            | HTTP
                            v
                  +-------------------+
                  |     AWS EC2       |
                  |  Amazon Linux     |
                  +---------+---------+
                            |
                            | Puerto 8080
                            v
                  +-------------------+
                  |  Docker Engine    |
                  +---------+---------+
                            |
                            | 8080 -> 9000
                            v
                  +-------------------+
                  | Docker Container  |
                  | Spring Boot App   |
                  |      :9000        |
                  +-------------------+

## Resposabilidad de cada capa
- **Máquina virtual EC2:** proporciona recuersos aislados de cómputo, memoria, almacenamiento y red alquilados a través de AWS.
- **Contenedor Docker:** proporciona un entorno de ejecución portable que contiene la aplicación y sus dependencias.
- **Aplicación web Java:** recibe las solicitudes HTTP y proporciona la funcionalidad de la aplicación.
- **Security Group:** controla qué tráfico entrenate puede llegar a la máquina virtual EC2.

