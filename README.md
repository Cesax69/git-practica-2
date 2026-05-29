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

---

### 2. Crear `index.html` y comprobar el estado

```bash
git status
```

---

### 3. Añadir al stage y confirmar

```bash
git add index.html
git commit -m "agregar fichero index.html inicial"
```

---

### 4. Añadir `description.html` y modificar `index.html`

```bash
git status
git diff
```

---

### 5. Crear `TODO.txt` y comprobar que Git lo detecta

```bash
git status
```

---

### 6. Crear `.gitignore` y comprobar que `TODO.txt` desaparece

Contenido del fichero `.gitignore`:
```
TODO.txt
```

```bash
git status
```

---

### 7. Añadir y confirmar `.gitignore`

```bash
git add .gitignore
git commit -m "agregar gitignore para excluir tareas personales"
```

---

### 8. Log del repositorio local

```bash
git log --oneline --graph --all
```

---

## Parte 2 — Fork y Clon (`git-practica-2`)

### 9. Clonar el repositorio forkeado

```bash
git clone https://github.com/Cesax69/git-practica-2.git
```

---

### 10. Crear el fichero personal y subirlo

```bash
git add Cesax69.html
git commit -m "agregar pagina personal de Cesax69"
git push
```

---

### 11. Crear rama `develop` y subir cambios

```bash
git checkout -b develop
git status
git add *
git commit -m "agregar seccion de proyectos y respuestas del taller"
git push origin develop
```

---

### 12. Log final con ramas

```bash
git log --oneline --graph --all
```

---

### 13. Pull Request en GitHub

Desde GitHub: crear Pull Request de `develop → main` y fusionarlo.

---

## Archivos del repositorio

| Archivo | Descripción |
|---|---|
| [`Cesax69.html`](Cesax69.html) | Página personal del alumno |
| [`respuestas.md`](respuestas.md) | Respuestas a las 11 preguntas del taller |
| [`bitacora-git.html`](bitacora-git.html) | Visor interactivo de todos los comandos ejecutados |

---

## Capturas
<img width="502" height="132" alt="image" src="https://github.com/user-attachments/assets/1220baa5-0817-454b-978b-f6b78ac27e31" />

<img width="619" height="112" alt="image" src="https://github.com/user-attachments/assets/ea38a435-66c6-49e8-9daa-4cac57f2c406" />

<img width="753" height="425" alt="image" src="https://github.com/user-attachments/assets/068a779f-8511-4879-8bb1-4b74a95da063" />


---

*Taller Git · Práctica 2 · César Enrique Garay García · 2026*
