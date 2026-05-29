# Taller Git · Práctica 2

**Alumno:** César Enrique Garay García  
**GitHub:** [@Cesax69](https://github.com/Cesax69)

Repositorio para la **Práctica 2 del Taller de Git**. Contiene el registro de comandos ejecutados, capturas de terminal y las respuestas al cuestionario.

---

## Parte 1 — Repositorio Local (`practica-taller-git`)

### 1. Inicializar el repositorio

```bash
git init
```

> **Captura:** resultado del comando `git init` mostrando la ruta del repositorio inicializado.

---

### 2. Crear `index.html` y comprobar el estado

```bash
git status
```

> **Captura:** `git status` mostrando `index.html` como fichero **untracked** (en rojo).

---

### 3. Añadir al stage y confirmar

```bash
git add index.html
git commit -m "agregar fichero index.html inicial"
```

> **Captura:** resultado del `git commit` con el hash del commit y `1 file changed`.

---

### 4. Añadir `description.html` y modificar `index.html`

```bash
git status
git diff
```

> **Captura 1:** `git status` mostrando `index.html` como **modified** (amarillo) y `description.html` como **untracked** (rojo).  
> **Captura 2:** `git diff` mostrando las líneas nuevas en verde dentro de `index.html`.

---

### 5. Crear `TODO.txt` y comprobar que Git lo detecta

```bash
git status
```

> **Captura:** `git status` mostrando `TODO.txt` como **untracked**.

---

### 6. Crear `.gitignore` y comprobar que `TODO.txt` desaparece

Contenido del fichero `.gitignore`:
```
TODO.txt
```

```bash
git status
```

> **Captura:** `git status` mostrando únicamente `.gitignore` como untracked — `TODO.txt` ya **no aparece**.

---

### 7. Añadir y confirmar `.gitignore`

```bash
git add .gitignore
git commit -m "agregar gitignore para excluir tareas personales"
```

> **Captura:** resultado del commit.

---

### 8. Log del repositorio local

```bash
git log --oneline --graph --all
```

> **Captura:** historial de commits del repositorio `practica-taller-git`.

---

## Parte 2 — Fork y Clon (`git-practica-2`)

### 9. Clonar el repositorio forkeado

```bash
git clone https://github.com/Cesax69/git-practica-2.git
```

> **Captura:** salida del `git clone` con los objetos descargados.

---

### 10. Crear el fichero personal y subirlo

```bash
git add Cesax69.html
git commit -m "agregar pagina personal de Cesax69"
git push
```

> **Captura:** resultado del `git push` mostrando la rama `main` actualizada en el remoto.

---

### 11. Crear rama `develop` y subir cambios

```bash
git checkout -b develop
git status
git add *
git commit -m "agregar seccion de proyectos y respuestas del taller"
git push origin develop
```

> **Captura 1:** `git checkout -b develop` confirmando el cambio de rama.  
> **Captura 2:** `git push origin develop` con `* [new branch] develop -> develop`.

---

### 12. Log final con ramas

```bash
git log --oneline --graph --all
```

> **Captura:** grafo de commits mostrando `main` y `develop`.

---

### 13. Pull Request en GitHub

> **Captura:** pantalla de GitHub mostrando el Pull Request de `develop → main` antes de fusionar.  
> **Captura:** confirmación del merge exitoso.

---

## Archivos del repositorio

| Archivo | Descripción |
|---|---|
| [`Cesax69.html`](Cesax69.html) | Página personal del alumno |
| [`respuestas.md`](respuestas.md) | Respuestas a las 11 preguntas del taller |
| [`bitacora-git.html`](bitacora-git.html) | Visor interactivo de todos los comandos ejecutados |

---

*Taller Git · Práctica 2 · César Enrique Garay García · 2026*
