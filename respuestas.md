# Respuestas - Taller Git · Práctica 2
**Alumno:** César Enrique Garay García  
**Usuario GitHub:** Cesax69  
**Fecha:** Mayo 2026

---

## Preguntas y Respuestas

---

### Pregunta 1
**¿Qué sucede cuando hacemos un `git add`?**

### Respuesta
Cuando ejecutamos `git add`, le indicamos a Git que queremos **incluir los cambios de un fichero en el próximo commit**. Este comando mueve los ficheros (o los cambios dentro de ellos) desde el **directorio de trabajo** (Working Directory) hacia el **área de preparación o stage** (también llamado Staging Area o Index).

Es importante entender que `git add` **no guarda los cambios de forma permanente** — solo los marca como "listos para confirmar". Es como preparar los ingredientes en la mesa antes de cocinar: aún no has cocinado, pero ya tienes todo listo.

```bash
# Añadir un fichero específico
git add index.html

# Añadir todos los ficheros modificados
git add .
```

---

### Pregunta 2
**¿Qué sucede cuando hacemos un `git commit`? ¿Dónde está ese commit?**

### Respuesta
Al ejecutar `git commit`, Git toma una **instantánea (snapshot) permanente** de todos los ficheros que estaban en el Staging Area y los guarda en el **historial del repositorio local**. Cada commit tiene un identificador único (hash SHA-1), el nombre del autor, la fecha y un mensaje descriptivo.

**¿Dónde está ese commit?** Después de hacer `git commit`, el commit reside **únicamente en el repositorio local** de tu máquina, dentro de la carpeta `.git/`. No ha viajado a ningún servidor externo todavía.

```bash
git commit -m "descripción clara de los cambios realizados"
```

El historial de commits se puede consultar con:
```bash
git log --oneline
```

---

### Pregunta 3
**¿Por qué al hacer `git commit` todavía no está disponible ese commit en el repositorio remoto?**

### Respuesta
Porque Git es un **sistema de control de versiones distribuido**. Esto significa que cada desarrollador tiene una copia completa e independiente del repositorio en su propia máquina. El comando `git commit` solo actúa sobre la copia **local**: registra el cambio en la base de datos interna de Git (carpeta `.git/`) pero **no establece ninguna comunicación con internet ni con el servidor remoto** (GitHub, GitLab, etc.).

El repositorio remoto y el local son dos entidades separadas. El commit existe en tu máquina pero GitHub no sabe de él hasta que tú decidas enviárselo explícitamente.

---

### Pregunta 4
**¿Qué hay que hacer para que veamos este commit en nuestro repositorio remoto de GitHub?**

### Respuesta
Para que el commit sea visible en GitHub, hay que **sincronizar el repositorio local con el remoto** usando el comando:

```bash
git push origin main
```

O simplemente `git push` si ya se ha configurado el upstream. Este comando **sube los commits locales** que aún no existen en el servidor remoto (origin) hacia la rama indicada (`main`). A partir de ese momento, el commit será visible públicamente (o para los colaboradores) en GitHub.

Si es la primera vez, puede ser necesario:
```bash
git push -u origin main
```
El parámetro `-u` establece el seguimiento (upstream) para que en el futuro baste con escribir solo `git push`.

---

### Pregunta 5
**¿Qué diferencia hay entre hacer un fork o crear una nueva rama?**

### Respuesta

| Característica | Fork | Nueva Rama |
|---|---|---|
| **Dónde existe** | Es una **copia independiente del repositorio** en tu propia cuenta de GitHub | Es una **línea de desarrollo paralela** dentro del mismo repositorio |
| **Propósito** | Contribuir a un proyecto ajeno o tener tu propia versión pública | Trabajar en una funcionalidad o bugfix de forma aislada |
| **Relación con el original** | Se puede vincular para enviar Pull Requests al repositorio original | Siempre pertenece al mismo repositorio |
| **Caso de uso típico** | Contribuir a proyectos open source | Desarrollo en equipo con Git Flow |

**En resumen:** Un **fork** es una copia de todo el repositorio en otra cuenta; una **rama** es una bifurcación del historial dentro del mismo repositorio.

---

### Pregunta 6
**¿Qué comando se utiliza para crear una nueva rama sin cambiarte a ella?**

### Respuesta

```bash
git branch nombre-de-la-rama
```

Este comando **crea la rama** pero te mantiene en la rama actual. Si quieres crear la rama Y cambiarte a ella al mismo tiempo, el comando es:

```bash
git checkout -b nombre-de-la-rama
# O con la sintaxis moderna:
git switch -c nombre-de-la-rama
```

---

### Pregunta 7
**¿Cuál es la diferencia entre los comandos `git switch` y `git checkout` al trabajar con ramas?**

### Respuesta

Ambos comandos permiten cambiar de rama, pero tienen diferencias importantes:

| Aspecto | `git checkout` | `git switch` |
|---|---|---|
| **Versión** | Comando clásico (disponible siempre) | Introducido en Git 2.23 (2019) |
| **Propósito** | Multifunción: cambia ramas, restaura ficheros, crea ramas | Específico para operaciones con ramas |
| **Claridad** | Puede ser confuso al usarse para múltiples cosas | Más claro e intuitivo al tener un único propósito |
| **Crear y cambiar** | `git checkout -b nueva-rama` | `git switch -c nueva-rama` |
| **Solo cambiar** | `git checkout nombre-rama` | `git switch nombre-rama` |

**Recomendación actual:** Git recomienda usar `git switch` para gestionar ramas y reservar `git checkout` para restaurar ficheros o cuando se necesite compatibilidad con versiones antiguas de Git.

---

### Pregunta 8
**¿Qué es una rama por defecto (como `main` o `master`) y por qué es importante?**

### Respuesta
La **rama por defecto** es la rama principal del repositorio — la que se crea automáticamente al inicializar el repositorio con `git init`. Históricamente se llamaba `master`, pero GitHub y la comunidad adoptaron `main` como nombre estándar más inclusivo desde 2020.

**¿Por qué es importante?**
- Es la **rama de referencia** del proyecto: contiene el código estable y en producción.
- Es la rama que ve el mundo cuando visita tu repositorio en GitHub.
- En proyectos en equipo, todas las demás ramas (develop, feature/x, hotfix/y) eventualmente se **fusionan con main** una vez que los cambios han sido revisados y aprobados.
- Actúa como el **punto de partida oficial** desde el que se crean todas las demás ramas.

---

### Pregunta 9
**¿Qué comando te permite ver la lista de todas las ramas locales de tu repositorio?**

### Respuesta

```bash
git branch
```

La rama activa se mostrará marcada con un asterisco `*`. Para ver también las ramas remotas:

```bash
git branch -a
```

Para ver solo las ramas remotas:

```bash
git branch -r
```

---

### Pregunta 10
**En el contexto de Git, explica con tus propias palabras qué es una rama (branch) y cuál es su beneficio principal al trabajar en un proyecto de software.**

### Respuesta
Imagina que el historial de tu proyecto es una línea del tiempo. Una **rama** es como abrir una **línea del tiempo alternativa**: puedes hacer cambios, experimentar, romper cosas y probar nuevas ideas sin que nada de eso afecte a la línea del tiempo principal (main).

Cuando tu experimento funciona y estás satisfecho con los cambios, puedes **fusionar** esa línea alternativa de vuelta a la principal mediante un `git merge` o un Pull Request.

**Beneficio principal:** Permiten que múltiples desarrolladores (o incluso uno solo) trabajen en diferentes funcionalidades o correcciones al mismo tiempo, de forma completamente aislada, sin pisarse ni romper el código estable del proyecto. Esto hace el desarrollo más rápido, seguro y organizado.

---

### Pregunta 11
**¿Qué ha pasado con el contenido de la carpeta `practica-taller-git`? ¿Por qué no la podemos ver en nuestro repositorio remoto de GitHub?**

### Respuesta
La carpeta `practica-taller-git` **no aparece en GitHub** porque es un **repositorio Git completamente independiente** — tiene su propia carpeta `.git/` interna. Cuando intentas añadir una carpeta que ya es un repositorio Git dentro de otro repositorio Git, Git la trata como un **submódulo** o simplemente la ignora como directorio sin rastrear sus contenidos internos.

En este caso, el repositorio principal (portafolio en `practica/`) y el de la práctica (`practica-taller-git/`) son dos repositorios separados con historiales y orígenes remotos distintos. Para que `practica-taller-git` apareciera en GitHub bajo el mismo repositorio, habría que:

1. **Eliminar la carpeta `.git/` interna** y añadir sus ficheros al repositorio padre (perdiéndose el historial de esa práctica).
2. **Configurarla como un submódulo de Git** con `git submodule add`.
3. **Subir `practica-taller-git` como su propio repositorio independiente** a GitHub.

La opción correcta para esta práctica sería la **3**: crear un repositorio separado en GitHub para `practica-taller-git` y hacer `git push` desde dentro de esa carpeta hacia su propio remoto.

---

*Taller Git · Práctica 2 · César Enrique Garay García · Cesax69*
