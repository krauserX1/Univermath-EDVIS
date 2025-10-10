# 🌿 Guía de Git Flow

El término **Git Flow** (a veces escrito *git-flow*) se refiere a una **estrategia de ramificación** (*branching model*) para gestionar el desarrollo de software con Git.  
No es una herramienta nueva, sino **una forma estructurada de organizar las ramas, los commits y los lanzamientos de versiones** dentro de un proyecto.

---

## 🧭 ¿Qué es Git Flow?

**Git Flow** es un modelo de trabajo propuesto por *Vincent Driessen* en 2010 que define **cómo y cuándo crear, usar y fusionar ramas** en un repositorio Git.

Objetivos principales:
- Mantener un **flujo de desarrollo limpio y organizado**.  
- Separar el **código en desarrollo**, **el código en pruebas** y **las versiones estables**.  
- Facilitar el manejo de **versiones y lanzamientos** (releases).  

---

## 🧭 Estructura principal de ramas

Git Flow utiliza **cinco tipos principales de ramas**:

| Rama | Propósito | Ejemplo |
|------|------------|----------|
| **main** (o *master*) | Contiene el código **estable y en producción**. Cada versión liberada se etiqueta con un *tag* (p. ej. `v1.0.0`). | `main` |
| **develop** | Contiene el código **en desarrollo activo**. Se fusionan aquí las nuevas características antes de liberar una versión. | `develop` |
| **feature/** | Se usan para desarrollar **nuevas funcionalidades**. Se crean desde `develop` y se fusionan de nuevo ahí. | `feature/login`, `feature/dashboard` |
| **release/** | Se crean para preparar una **nueva versión estable**, corrigiendo errores o ajustando detalles antes de publicarla. | `release/1.2.0` |
| **hotfix/** | Se usan para **corregir errores críticos en producción**. Se crean desde `main` y se fusionan tanto en `main` como en `develop`. | `hotfix/fix-login` |

---

## 🔄 Flujo de trabajo básico

```text
main ────────────●────────────●──────────────▶ (v1.0.0, v1.1.0)
                   ╲          ╱
develop ───────────●────────●──────────────▶ (preparación)
                     ╲     ╱
feature/login ───────●───●──▶ Merge
release/1.2.0 ───────●─────▶ Merge
hotfix/urgent-fix ───●────▶ Merge
```

### Ejemplo de flujo:

1. Crear rama de funcionalidad:
```bash
git checkout develop
git checkout -b feature/login
```
2. Trabajar y hacer commits:
```bash
git commit -m "feat(auth): agregar login con JWT"
```
3. Fusionar la funcionalidad cuando esté lista:
```bash
git checkout develop
git merge feature/login
```
4. Crear rama de *release*:
```bash
git checkout -b release/1.1.0
```
5. Fusionar a `main` cuando se publique:
```bash
git checkout main
git merge release/1.1.0
git tag -a v1.1.0 -m "Versión 1.1.0"
```
6. Corregir error en producción con *hotfix*:
```bash
git checkout -b hotfix/fix-login
git commit -m "fix(login): corregir error en autenticación"
git merge hotfix/fix-login main
git merge hotfix/fix-login develop
```

---

## ⚙️ Herramienta CLI: `git-flow`

Se puede instalar con:

```bash
# Linux
sudo apt install git-flow

# macOS
brew install git-flow-avh
```

Inicializar en un repositorio:

```bash
git flow init
```

Comandos comunes:

```bash
git flow feature start login
git flow feature finish login
git flow release start 1.1.0
git flow release finish 1.1.0
```

---

## 🔗 Git Flow + Conventional Commits

Se complementan perfectamente:

- Ramas tipo `feature/`, `fix/`, `hotfix/`.  
- Commits respetan la convención (`feat:`, `fix:`, `chore:`, etc.).  
- Al fusionar a `main`, herramientas como *Semantic Release* pueden:
  - Detectar tipo de cambio.  
  - Incrementar versión según SemVer.  
  - Generar `CHANGELOG.md`.  
  - Crear tag automático (`v1.2.0`, etc.).

Ejemplo:

| Rama | Commit ejemplo | Versión resultante |
|-------|----------------|--------------------|
| `feature/payment` | `feat(payment): agregar integración con PayPal` | `1.1.0` |
| `hotfix/login` | `fix(auth): corregir validación del token` | `1.0.1` |
| `release/2.0.0` | `feat(api)!: cambiar formato de respuesta` | `2.0.0` |

---

## ✅ Ventajas de Git Flow

- Estructura clara del desarrollo.  
- Control sobre qué entra a producción.  
- Ideal para equipos medianos o grandes.  
- Compatible con Conventional Commits y Semantic Versioning.

---

## ⚠️ Desventajas

- Puede ser pesado para proyectos pequeños o con despliegues continuos.  
- Requiere disciplina para mantener la coherencia entre ramas y commits.
