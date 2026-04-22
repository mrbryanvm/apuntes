# Trabajo Individual - Curso de Git
**Nombre:** [Bryan Vasquez Maldonado]
**Correo:** [bryan.vasquez.456@gmail.com]

---

## Clase 1: Introducción y Fundamentos de Git

En esta primera sesión se cubrieron los conceptos básicos de Git, su origen histórico y la configuración inicial del entorno de trabajo.

### 1. ¿Qué es Git?
Git es un **sistema de control de versiones distribuido**. Su función principal es crear "puntos de guardado" (checkpoints) de los archivos de un proyecto para:
* Mantener un historial de cambios.
* Volver atrás en el tiempo en caso de errores.
* Trabajar de forma colaborativa sin sobrescribir el trabajo de otros.

### 2. Historia y Origen
Git fue creado por **Linus Torvalds** en 2005. El motivo de su creación fue un conflicto con el software *BitKeeper* (que usaban para el Kernel de Linux). Tras perder el acceso gratuito, Linus decidió programar su propia herramienta de control de versiones en aproximadamente dos semanas, enfocándose en la velocidad, integridad de datos y soporte para flujos de trabajo no lineales.

### 3. Instalación y Configuración
Durante la clase, realizamos la instalación en Windows y Linux. Los comandos esenciales de configuración global son:

```bash
# Configurar la identidad del usuario
git config --global user.name "Tu Nombre"
git config --global user.email "tucorreo@ejemplo.com"

# Verificar la configuración
git config --list
