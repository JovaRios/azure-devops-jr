# 🚀 DevOps Jr Project – Azure + Docker + GitHub Actions

Proyecto DevOps orientado a perfil **Junior**, enfocado en la construcción de un **pipeline CI/CD** para desplegar una aplicación contenerizada en **Azure App Service**, utilizando **Docker Hub** como registry y **GitHub Actions** para automatización.

---

## 📌 Objetivo del proyecto
Implementar un flujo completo **end-to-end** que permita:
- Construir imágenes Docker de forma automatizada
- Resolver compatibilidad ARM → AMD64
- Publicar imágenes en Docker Hub
- Desplegar la aplicación en Azure App Service Linux
- Validar el comportamiento real de actualización de contenedores

---

## 🧱 Arquitectura
Developer
↓
GitHub Repository
↓ (push)
GitHub Actions (CI)
↓
Docker Buildx (linux/amd64)
↓
Docker Hub
↓
Azure App Service (Linux Container)


---

## ⚙️ Tecnologías utilizadas
- **Docker & Dockerfile**
- **Docker Hub**
- **GitHub Actions**
- **Azure App Service (Linux)**
- **Azure CLI**
- **Nginx**
- **Linux**

---

## 🌐 Aplicación
La aplicación es un contenedor Docker que utiliza **Nginx** como servidor web para servir contenido estático.

**Rol de Nginx:**
- Servidor HTTP ligero y eficiente
- Escucha en el puerto 80
- Sirve contenido estático desde `/usr/share/nginx/html`
- Ideal para contenedores por su bajo consumo de recursos

---

## 🐳 Construcción de la imagen Docker
Debido a que el entorno de desarrollo es **macOS ARM (M1)** y Azure App Service utiliza **AMD64**, se utiliza `docker buildx` para asegurar compatibilidad:

```bash
docker buildx build \
  --platform linux/amd64 \
  -t jovanyrios/devops-jr-app:latest \
  --push .
