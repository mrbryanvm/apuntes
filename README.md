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

### 3. Configuración: Global vs. Local (Jerarquía)

Si estás usando tu segunda cuenta de GitHub para un proyecto, necesitas que los commits salgan con ese nombre y correo, no con los de tu cuenta principal.

- **Global (`git config --global user.name`)**: Aplica para toda la computadora. Es la configuración por defecto.
- **Local (`git config user.name`)**: Se ejecuta sin la palabra `--global` dentro de la carpeta de un proyecto específico.

> 💡 **La regla de oro:** La configuración Local siempre le gana a la Global. Así evitas que un proyecto de trabajo salga con tu apodo de gamer de tu cuenta personal.

### 4. git checkout: La Máquina del Tiempo

Este comando te permite mirar el historial de tu proyecto como si viajaras al pasado.

**¿Cómo viajar?**
Haces un `git log --oneline`, copias el Hash (los numeritos amarillos de un commit antiguo) y escribes `git checkout <hash>`.

**El estado "Detached HEAD" (Cabeza Desacoplada):**
No te asustes con este término. "HEAD" es simplemente hacia dónde está mirando Git. Normalmente, HEAD apunta a la punta de una rama (como `main`). Si viajas al pasado a un commit específico, tu "cabeza" se suelta de la rama actual. Estás en modo "fantasma espectador".

**Las Reglas del Viaje en el Tiempo:**

- **Mira pero no toques:** Usa esto solo para ver código antiguo o recuperar un archivo borrado. Si haces un commit en este estado, se perderá en el limbo a menos que crees una rama nueva (`git checkout -b nueva_rama`).
- **Piso limpio:** Git no te dejará viajar al pasado si tienes archivos modificados sin guardar (en rojo o verde). Haz commit antes de viajar.
- **Regreso al futuro:** Para volver a la normalidad, simplemente escribe `git checkout main`.

---

## 🌿 Clase 5: Ramas (Branches) y Flujo de Trabajo

### 1. El Tema Central: RAMAS (Branches)
Las ramas son bifurcaciones del estado del código. Imagina que creas un camino paralelo para trabajar sin arruinar lo que ya funciona.

**¿Para qué sirven?**
- **Seguridad:** Tocas el código sin miedo a romper la versión principal.
- **Trabajo en Equipo:** Cada integrante puede trabajar en su parte de forma aislada.
- **Experimentación:** Puedes probar cosas locas y, si no funcionan, simplemente borras la rama.

### 2. Comandos de Gestión:
- `git branch`: Lista todas las ramas y te marca con un asterisco (`*`) en la que estás actualmente.
- `git branch <nombre>`: Crea una nueva rama desde donde estás parado.
- `git branch -D <nombre>`: Elimina una rama (úsalos con cuidado).
- `git checkout <nombre>`: Te mueve a la rama especificada.
- `git checkout -b <nombre>`: Comando "pro"; crea la rama y te cambia a ella de inmediato.
- `git switch <nombre>`: Versión moderna y específica de `checkout` para cambiar de rama.
- `git switch -c <nombre>`: Crea una rama y se cambia a ella (igual que `checkout -b`).

### 3. 🌊 Flujo de Trabajo: GitFlow
Para no hacer un "chiquero" de ramas, usamos un estándar. GitFlow define qué nombre y qué función tiene cada rama.

**Tipos de Ramas en GitFlow:**
- **Main (Producción):** Solo tiene el código que funciona al 100%. Generalmente empieza con el `initial commit`.
- **Develop (Desarrollo):** El "campo de juego". Aquí se integran todas las nuevas funciones antes de pasar a `main`.
- **Feature branches (feature/<nombre>):** Ramas temporales para crear una funcionalidad específica (ej: `feature/login`). Al terminar, se integran a `develop` y se borran.
- **Release:** Ramas de prueba (QA) para pulir errores antes del lanzamiento oficial.
- **Hotfix:** Arreglos de emergencia que se hacen directamente sobre el código de producción (`main`) cuando algo explota.

### 4. 🤝 Colaboración en GitHub
Para que tus amigos no solo miren tu código sino que también metan mano:

1. Ve a tu repositorio en GitHub.
2. Ve a **Settings** > **Collaborators**.
3. Haz clic en el botón **Add People** e ingresa el *username* o correo de tu compañero.
4. ⚠️ **Importante:** Tu compañero debe aceptar la invitación que le llegará por correo.

> 💡 **Tip de la clase:** El comando `git log --oneline --graph --all` es tu mejor amigo para ver visualmente cómo se están cruzando y separando tus ramas.

---

## 🔀 Clase 6: Fusión y Sincronización (Merge, Fetch, Pull, Push)

En esta sesión abordamos los comandos fundamentales para sincronizar nuestro repositorio local con el remoto y cómo integrar los cambios de diferentes ramas.

### 1. ¿Qué es `git merge`?
Merge significa **fusión**. Este comando nos permite fusionar nuestras ramas en una sola para que ambas compartan los commits y el historial de cambios.

- **Flag `--no-ff` (No Fast Forward):** Al utilizar `git merge --no-ff <rama>`, Git fuerza la creación de un nuevo commit específico para la fusión. Esto es sumamente útil porque evita que se pierda el historial visual de las ramas, incluso si decides borrar la rama original después.

### 2. ¿Qué es `git fetch`?
Es el comando que permite verificar si hubo cambios en la rama remota y sus ramas hijas. Actúa como un radar: se comunica con GitHub (o tu servidor remoto) y te avisa si hay actualizaciones nuevas sin modificar tu código local.

### 3. ¿Qué es `git pull`?
El comando `git pull` permite traer todos los cambios que tiene el repositorio remoto de una rama y los fusiona automáticamente con tu rama local actual. Es recomendable usarlo especificando el origen y la rama para evitar problemas:

```bash
git pull origin rama
```

### 4. ¿Qué es `git push`?
Es el comando que sube (empuja) tus cambios locales al repositorio remoto. Al igual que el pull, se recomienda ser explícito con la rama:

```bash
git push origin rama
```

> 💡 **Nota sobre el flag `-u` (upstream):** La primera vez que subes una rama nueva que no existe en el repositorio remoto, debes usar el flag `-u`. Esto establece una conexión directa y le dice a Git adónde debe enviar futuros cambios por defecto.
> ```bash
> git push -u origin rama
> ```

### 5. Flujo de Trabajo (Sin Pull Requests)
A continuación se detalla un ciclo de trabajo típico al colaborar en equipo integrando cambios directamente en la rama de desarrollo, sin utilizar interfaces web (como los Pull Requests de GitHub):

```bash
# 1. Posicionarse y actualizar la rama base
git checkout develop
git fetch
git pull origin develop

# 2. Ir a la rama de trabajo
git checkout rama

# 3. Traer actualizaciones de develop a tu rama (solo si hubo cambios)
git merge develop 

# --- AQUI TRABAJAS EN TU RAMA (add, commit, etc.) ---

# 4. Subir tus cambios (usa -u si es la primera vez)
git push origin rama 

# 5. Volver a develop para la integración final
git checkout develop
git fetch
git pull origin develop

# 6. Fusionar tu rama asegurando el historial (no fast-forward)
git merge --no-ff rama

# 7. Resolver manualmente los archivos fallidos y sus conflictos (si los hay)
git add .
git commit
# (Guardar y cerrar en el editor, ej: Ctrl+O, Enter, Ctrl+X si usas nano)

# 8. Limpieza y subida final
git branch -D rama          # Borras la rama local
git push origin develop     # Subes los cambios integrados al remoto
```

---

## 🤝 Clase 7: Pull Requests y Colaboración Segura

### 1. ¿Qué son los Pull Request?
También informalmente llamados (PRs), es la forma profesional de trabajar con git/github, crea un request en el grupo del repositorio en github que permite ver que se quiere mergear o unir al código base que ya se tiene.

### 2. ¿Cómo crear un PR?
Para ello primero una vez que hagas `git push origin rama` debes dirigirte a github.com y seguir los pasos del siguiente tutorial:
[Ver tutorial](https://youtu.be/4CeMKqloOJc)

### 3. Flujo de trabajo (Con Pull Requests)
```bash
git checkout develop
git fetch
git pull origin develop
git checkout rama # Agregas -b si estás creando la rama
git merge develop # Solo si hubo cambios en develop
# Trabajas en tu rama
git push origin rama # Agregas -u si es la primera vez que subes cambios al repositorio remoto
git checkout develop
git fetch
git checkout rama
git merge develop # Solo si hubo cambios en develop antes de hacer la PR
# Resuelves manualmente los archivos fallidos y sus conflictos
git add .
git commit
# [Ctrl + O, Enter, Ctrl + X] (depende si usan nano)
git push origin rama
# Sigues el flujo mostrado en “¿Cómo crear un PR?"
```

### 4. ¿Por qué usamos los PRs sí ya podemos trabajar normalmente sin ellos?
Los usamos por temas de seguridad, que cualquier colaborador pueda tocar nuestro repositorio y mergear sin preguntar o avisar es un riesgo constante, ¿Y si lo hace mal? ¿Y si está metiendo código malicioso? ¿Y si es un norcoreano intentando hackearme que solo se ganó mi confianza? ¿Qué código está pusheando?

Los PRs permite al equipo y lo fuerza a ver los cambios, limita la colaboración y obliga al debate y deliberación. Nos permite entender que vamos a poner en marcha, quien lo hara, presentar una opinión u oponerse al cambio, los PRs nos permiten un mejor manejo grupal de nuestro repositorio en equipo.

### 5. ¿Cómo proteger mi repositorio y limitar la colaboración?
Bien, ya sabemos la importancia de los PRs pero aun así, no hemos limitado nada, seguimos confiando en que nuestros colaboradores esperaran nuestra review y aprobación para unir su código, pero aún pueden hacerlo, porque no los hemos limitado, para eso lo que debemos hacer es lo que se detalla en el siguiente video corto:
[Ver tutorial](https://youtu.be/ZdLomug2-UQ)

### 6. ¿Cómo colaboro al proyecto si no soy un colaborador invitado?
En la clase nuestro querido postulante Andre colaboró sin estar invitado en nuestro repositorio sin estar invitado, esto es posible y nos lo explica él mismo en el siguiente video:
[En progreso]

---

## 🛠️ Clase 8: Comandos de Utilidad, Conflictos y Entregas Finales

### 1. Comandos de Utilidad (Lo nuevo)

#### Git Stash (El "Almacén Temporal")
Sirve para guardar cambios que no quieres commitear todavía pero necesitas "limpiar" tu área de trabajo para cambiar de rama.

- `git stash save "mensaje"` o `git stash`: Guarda tus cambios actuales en una pila.
- `git stash list`: Muestra la lista de todos los cambios guardados.
- `git stash pop`: Recupera el último cambio guardado y lo elimina de la lista.

#### Git Diff (Diferencias)
Para ver exactamente qué líneas cambiaste antes de hacer commit.

- `git diff`: Cambios en archivos que no has pasado al área de preparación (staged).
- `git diff --staged`: Cambios en archivos que ya están en el área de preparación.
- `git diff rama1 rama2`: Compara las diferencias totales entre dos ramas.

#### Commits Largos
Recuerda que para cambios complejos es mejor usar un título y una descripción detallada:
```bash
git commit -m "Título corto" -m "Descripción detallada de todos los cambios realizados"
```

### 2. ⚔️ Resolución de Conflictos y Pull Requests (PR)

**El problema de los PRs paralelos:**
Si dos personas tocan el mismo archivo (ej. `README.md`) y el PR #4 se acepta primero, el PR #5 automáticamente mostrará un "Merge Conflict". GitHub no te dejará mergear hasta que resuelvas el conflicto localmente.

**Pasos para resolverlo:**

1. Vuelve a tu rama local.
2. Haz un `git pull origin develop` para traer los cambios aceptados del otro PR.
3. Usa el Merge Editor de Visual Studio Code para elegir qué código se queda (Incoming, Current o ambos).
4. Haz commit de la resolución y sube los cambios (`git push`). El PR en GitHub se actualizará solo y te permitirá mergear.

> 💡 **Buena práctica:** Una vez que tu PR ha sido aceptado y mergeado en la web, dale al botón "Delete branch" en GitHub para mantener el repositorio limpio.

### 3. 🚀 Entregas Finales (Deadlines)

- **Individual (Apuntes + README personal):** Mañana viernes a las 21:30. Se revisará el link que pusiste en la lista oficial.
- **Grupal (Proyecto):** Sábado a las 21:00.

> ⚠️ **Regla de Oro:** No se tomarán en cuenta commits realizados después de las horas señaladas.