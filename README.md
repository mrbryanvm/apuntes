<div align="center">
  <h1>Trabajo Individual - Curso de Git</h1>
  <p><strong>Nombre:</strong> Bryan Vasquez Maldonado | <strong>Correo:</strong> bryan.vasquez.456@gmail.com</p>
</div>

---

## 📚 Clase 1: Introducción y Fundamentos de Git

En esta primera sesión se cubrieron los conceptos básicos de Git, su origen histórico y la configuración inicial del entorno de trabajo.

### 1. ¿Qué es Git?

> Git es un **sistema de control de versiones distribuido**. 

Su función principal es crear "puntos de guardado" (checkpoints) de los archivos de un proyecto para:
- 🗂️ Mantener un historial de cambios.
- ⏪ Volver atrás en el tiempo en caso de errores.
- 🤝 Trabajar de forma colaborativa sin sobrescribir el trabajo de otros.

<!-- ESPACIO PARA IMAGEN 1: Te sugiero poner aquí un diagrama de cómo funciona un sistema distribuido o el logo oficial de Git -->
<div align="center">
  <img src="https://www.20i.com/blog/wp-content/uploads/2022/08/git-blog-header.png" alt="Diagrama de Git o Logo" width="500">
  <br>
  <em><small>Logo de git</small></em>
</div>

### 2. Historia y Origen
Git fue creado por **Linus Torvalds** en 2005. El motivo de su creación fue un conflicto con el software *BitKeeper* (que usaban para el Kernel de Linux). Tras perder el acceso gratuito, Linus decidió programar su propia herramienta de control de versiones en aproximadamente dos semanas, enfocándose en:
- ⚡ Velocidad
- 🔒 Integridad de datos
- 🔀 Soporte para flujos de trabajo no lineales

### 3. Instalación y Configuración
Durante la clase, realizamos la instalación en Windows y Linux. Los comandos esenciales de configuración global son:

```bash
# Configurar la identidad del usuario
git config --global user.name "Tu Nombre"
git config --global user.email "tucorreo@ejemplo.com"

# Verificar la configuración
git config --list
```

---

## ⚙️ Clase 2: Estados y Commits

Para entender cómo trabaja Git, es fundamental conocer el flujo de los archivos a través de sus tres estados principales antes de llegar a la nube.

### 1. Los Tres Estados de Git

- 📁 **Directorio de Trabajo (Working Directory):** Es tu carpeta local donde creas o modificas código. Aquí los cambios aún no están "asegurados" por Git.
- 📝 **Área de Preparación (Staging Area):** Un área temporal donde seleccionas qué cambios específicos quieres incluir en tu siguiente punto de guardado.
- 📦 **Repositorio Local:** El historial confirmado. Aquí los cambios reciben un ID único (hash) y ya forman parte oficial de la historia del proyecto.

<!-- ESPACIO PARA IMAGEN 2: Aquí es ideal colocar un diagrama visual de los tres estados de Git (Working Directory -> Staging Area -> Local Repo) -->
<div align="center">
  <img src="https://miro.medium.com/1*diRLm1S5hkVoh5qeArND0Q@2x.png" alt="Flujo de los Tres Estados de Git" width="600">
  <br>
  <em><small>git flow</small></em>
</div>

### 2. Directorio de Trabajo: Untracked vs Modified

Git observa tu carpeta y cataloga los archivos en dos condiciones principales:
- 🆕 **Untracked (Sin seguimiento):** Archivos nuevos que Git ve pero de los que no tiene una versión previa.
- ✏️ **Modified (Modificado):** Archivos que Git ya conocía pero que han sufrido cambios, eliminaciones o han sido renombrados.

### 3. Recuperación de Archivos

Si cometemos un error en el directorio de trabajo y queremos volver al estado original del archivo, usamos:
```bash
git restore <archivo>
```
> ⚠️ **Atención:** Esto borra físicamente lo que escribiste para regresar al último estado guardado. Se debe usar con precaución.

### 4. Ignorar Archivos con `.gitignore`

No todo debe subirse al repositorio (ej. contraseñas, carpetas de dependencias como `node_modules` o archivos de configuración personal).
Para evitarlo, creamos un archivo llamado `.gitignore` y escribimos dentro los nombres o extensiones de archivos que queremos que Git ignore por completo.

### 5. Preparando Cambios (Stage Area)

Este estado intermedio nos permite ser selectivos con lo que guardamos:
- `git add <archivo>`: Agrega un archivo específico al stage.
- `git add .`: Agrega todos los archivos modificados de la carpeta actual.
- `git restore --staged <archivo>`: Saca un archivo del área de preparación para devolverlo al estado modificado (sin borrar el código).

### 6. Confirmar Cambios (Repositorio Local)

Es la fase final donde los cambios en *staged* se graban en el historial de manera oficial.
- `git commit -m "mensaje"`: Crea el punto de guardado con una descripción.
- `git reset --soft HEAD~1`: Deshace el último commit realizado, manteniendo tus cambios en el área de preparación por si necesitas corregir algo.

### 7. Buenas Prácticas: Commits Atómicos

Un **commit atómico** es aquel que representa un único cambio lógico, pequeño y completo.

- ✅ Haz commits a menudo pero con sentido.
- ❌ No subas código que deje la aplicación sin funcionar.
- ✍️ Usa verbos imperativos: **Add, Change, Fix, Remove**.
- 🚫 No uses punto final ni puntos suspensivos en el mensaje del commit.
- 📏 Mantén el título bajo los 50 caracteres para que sea conciso.

### 8. Commits Semánticos (Conventional Commits)

Para que el historial sea fácilmente legible, usamos el formato `<tipo>: <descripción>`.

- ✨ **feat**: Nueva característica.
- 🐛 **fix**: Solución de un error.
- 📚 **docs**: Cambios en la documentación.
- 💅 **style**: Cambios de formato (espacios, puntos y coma) que no afectan la lógica.
- ♻️ **refactor**: Cambio en el código que no corrige errores ni añade funciones (ej. renombrar variables).
- 🧪 **test**: Añadir o corregir pruebas.

> 💡 **Tip:** Si se necesita más espacio, se deja una línea en blanco tras el título y se añade un **cuerpo** con todo el contexto necesario.

<!-- ESPACIO PARA IMAGEN 3: Una captura de pantalla de un historial de commits limpios (usando git log o una interfaz gráfica como GitKraken/GitHub) mostrando commits semánticos -->
<div align="center">
  <img src="https://miro.medium.com/v2/resize:fit:1400/1*izVKF4AT1iDtv4fJO8oWWA.png" alt="Ejemplo de Commits Semánticos en el Historial" width="600">
  <br>
  <em><small>Git log</small></em>
</div>

## Clase 3: GitHub, Configuración SSH y Repositorios Remotos

En esta sesión pasamos de la gestión local a la remota. El objetivo principal es conectar tu trabajo con GitHub para que sea accesible desde cualquier lugar y por cualquier persona (incluido el Auxiliar para calificarte).

### 1. Git vs. GitHub: No son lo mismo
Es el error más común de los novatos. Aquí la diferencia clara:
*   **Git:** Es la herramienta (el software) que gestiona tus commits y el historial de manera local en tu máquina.
*   **GitHub:** Es la plataforma web (la nube) que aloja tus repositorios de Git y te permite trabajar en equipo.


### 2. Creación de Cuenta y Repositorio
*   **Cuenta Personal vs. Institucional:** Se recomienda usar una cuenta personal. La cuenta universitaria se pierde al graduarse, y con ella, todos tus proyectos.
*   **Username:** Piénsalo bien; es permanente y es tu identidad como desarrollador.
*   **Crear el Repo:** En GitHub, ve a "New repository". Usa el nombre de tu carpeta local, déjalo en público y **no añadas** README ni `.gitignore` si ya los tienes creados localmente.

### 3. Configuración SSH (La Llave Maestra)
Configurar SSH es vital para no tener que escribir tu usuario y contraseña cada vez que quieras subir cambios (`git push`).

<div align="center">
  <img src="https://i.ytimg.com/vi/iVJesFfzDGs/maxresdefault.jpg" alt="Configuración SSH GitHub" width="600">
  <br>
  <em><small>Configuración SSH GitHub</small></em>
</div>

**Pasos para generar la llave:**
1. Abre la terminal (o Git Bash en Windows).
2. Ejecuta el comando:
   ```bash
   ssh-keygen -t ed25519 -C "tu-correo@ejemplo.com"
---
### 4. Conectando tu Repo Local al Remoto
Una vez tengas el repositorio creado en GitHub, copia la URL de SSH y ejecuta estos comandos en tu carpeta local:
```bash
# 1. Vincula tu carpeta local con el link de GitHub
git remote add origin git@github.com:tu-usuario/tu-repo.git
# 2. Asegúrate de que tu rama principal se llame "main"
git branch -M main
# 3. Sube tus cambios por primera vez
git push -u origin main
```

## 🌐 Clase 4: Conexiones Remotas, SSH Múltiple y "Viajes en el Tiempo"

### 1. git remote: El Arquero de Git

Piensa en `git remote` como un arquero. Tu código está en tu computadora (el arco), pero necesitas decirle a Git hacia dónde debe disparar la flecha (la nube/GitHub).

**¿Qué es el "Origin"?**
Cuando usas el comando `git remote add origin <URL>`, le estás diciendo a Git: "Oye, esta URL larguísima de GitHub a partir de ahora se va a llamar origin". Es solo un apodo (alias) para no tener que escribir el link completo cada vez que subes código.

**Comandos clave:**

- `git remote -v`: Te muestra exactamente a qué URLs está apuntando tu repositorio actual (tanto para subir `push` como para bajar `fetch` código).
- `git remote set-url origin <NUEVA_URL>`: Cambia el objetivo del arquero. Se usa si te equivocaste y clonaste con HTTPS en lugar de SSH, o si quieres mandar tu código a un repositorio totalmente distinto.

### 2. Múltiples Llaves SSH (El concepto "difícil")

¿Por qué fue confuso? Porque el concepto de SSH ya es abstracto.
La explicación simple: Una llave SSH es literalmente una llave digital. Cada cuenta de GitHub es como una casa diferente. Si tienes tu cuenta personal y una cuenta de la universidad/trabajo, necesitas dos llaves distintas (una para cada puerta).

El problema es que, por defecto, tu computadora agarra la primera llave que encuentra e intenta abrir todas las puertas con esa. Para arreglarlo, debemos crear un "llavero" organizado (el archivo `config`).

**Los pasos explicados:**

- **Crear la segunda llave:** Usas el comando `ssh-keygen` pero le agregas la bandera `-f` para darle un nombre diferente (ej. `id_ed25519_auxi`), así no borra la llave de tu cuenta principal.

- **El archivo config (El Llavero):** Entras a la carpeta oculta `.ssh` y creas un archivo llamado `config` (sin extensión). Adentro le dices a tu computadora cómo usar las llaves:

```plaintext
# Configuración para tu cuenta secundaria
Host github-auxi            <-- El "apodo" que usarás al clonar
  HostName github.com       <-- El servidor real de GitHub
  User git                  <-- Siempre es 'git'
  IdentityFile ~/.ssh/id_ed25519_auxi  <-- La ruta a tu SEGUNDA llave
```

**¿Cómo se usa en la práctica?**
Si antes clonabas un repositorio así: `git clone git@github.com:usuario/repo.git`
Ahora usas el "apodo" del Host que inventaste: `git clone git@github-auxi:usuario/repo.git`. La computadora lee `github-auxi`, va a tu archivo config, saca la llave correcta y te deja entrar sin pedir contraseñas.