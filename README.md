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


## Clase 2: Estados y Commits

[cite_start]Para entender cómo trabaja Git, es fundamental conocer el flujo de los archivos a través de sus tres estados principales antes de llegar a la nube[cite: 1, 3].

### 1. Los tres estados de Git
* **Directorio de Trabajo (Working Directory):** Es tu carpeta local donde creas o modificas código. [cite_start]Aquí los cambios aún no están "asegurados" por Git[cite: 5, 6].
* [cite_start]**Área de Preparación (Staging Area):** Un área temporal donde seleccionas qué cambios específicos quieres incluir en tu siguiente punto de guardado[cite: 7, 8].
* **Repositorio Local:** El historial confirmado. [cite_start]Aquí los cambios reciben un ID único (hash) y ya forman parte oficial de la historia del proyecto[cite: 9, 10].

### 2. Directorio de Trabajo: Untracked vs Modified
[cite_start]Git observa tu carpeta y cataloga los archivos en dos condiciones[cite: 19, 20]:
* [cite_start]**Untracked (Sin seguimiento):** Archivos nuevos que Git ve pero de los que no tiene una versión previa[cite: 21].
* [cite_start]**Modified (Modificado):** Archivos que Git ya conocía pero que han sufrido cambios, eliminaciones o renombrados[cite: 22].

### 3. Recuperación de archivos
[cite_start]Si cometemos un error en el directorio de trabajo y queremos volver al estado original del archivo, usamos[cite: 24, 25]:
* `git restore <archivo>`: Borra físicamente lo que escribiste para regresar al último estado guardado. [cite_start]Se debe usar con precaución[cite: 27, 28].

### 4. Ignorar archivos con .gitignore
[cite_start]No todo debe subirse al repositorio (ej. contraseñas, carpetas de dependencias como `node_modules` o archivos de configuración personal)[cite: 31, 61].
[cite_start]Para ello, creamos un archivo llamado `.gitignore` y escribimos dentro los nombres o extensiones de archivos que queremos que Git ignore por completo[cite: 32, 40].




### 5. Preparando cambios (Stage Area)
[cite_start]Este estado intermedio nos permite ser selectivos con lo que guardamos[cite: 47, 48].
* [cite_start]`git add <archivo>`: Agrega un archivo específico al stage[cite: 50].
* [cite_start]`git add .`: Agrega todos los archivos modificados de la carpeta actual[cite: 50].
* [cite_start]`git restore --staged <archivo>`: Saca un archivo del área de preparación para devolverlo al estado modificado (sin borrar el código)[cite: 51].

### 6. Confirmar cambios (Repositorio Local)
[cite_start]Es la fase final donde los cambios en *staged* se graban en el historial[cite: 52, 55].
* [cite_start]`git commit -m "mensaje"`: Crea el punto de guardado con una descripción[cite: 56].
* [cite_start]`git reset --soft HEAD~1`: Deshace el último commit realizado, manteniendo tus cambios en el área de preparación por si necesitas corregir algo[cite: 57, 58].
