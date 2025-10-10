# 🧭 Guía de Estilo — Conventional Commits

Los **Conventional Commits** establecen una convención simple y estandarizada para escribir mensajes de *commit*.  
Con ellos se mejora la legibilidad del historial, se facilita la generación automática de versiones y *changelogs*,  
y se mantiene un flujo de trabajo más organizado. 🚀

---

## 🧩 Estructura básica del commit

```bash
<tipo>(<ámbito>): <descripción breve>

[opcional cuerpo del mensaje]

[opcional pie del mensaje]
```

### 📌 Ejemplo

```bash
feat(auth): agregar validación de token JWT
```

```bash
fix(api): corregir error 500 al crear usuario
```

```bash
docs(readme): actualizar instrucciones de instalación
```

---

## 🏷️ Tipos de commit

| Tipo | Descripción | Ejemplo |
|------|--------------|----------|
| 🎉 **feat** | Nueva funcionalidad o característica. | `feat(login): agregar autenticación con Google` |
| 🐛 **fix** | Corrección de errores o *bugs*. | `fix(form): validar campos vacíos` |
| 📚 **docs** | Cambios en documentación. | `docs(readme): agregar pasos de instalación` |
| 💅 **style** | Cambios de formato o estilo (sin alterar lógica). | `style(ui): ajustar márgenes y espaciados` |
| 🧠 **refactor** | Reestructuración del código sin modificar su comportamiento. | `refactor(auth): simplificar lógica de validación` |
| ⚡ **perf** | Mejoras de rendimiento. | `perf(api): optimizar consultas SQL` |
| 🧪 **test** | Adición o actualización de pruebas. | `test(math): agregar casos de prueba para división` |
| 🏗️ **build** | Cambios en dependencias o configuración de compilación. | `build(deps): actualizar versión de express` |
| 🔁 **ci** | Cambios en la configuración de integración continua. | `ci(github): agregar flujo de despliegue` |
| 🔧 **chore** | Mantenimiento general (sin afectar código o pruebas). | `chore: limpiar archivos temporales` |
| ⏪ **revert** | Reversión de un commit anterior. | `revert: feat(login) agregar autenticación con Google` |

---

## 🎯 Ámbito (*scope*)

El **ámbito** indica la parte del proyecto afectada por el cambio.  
Es opcional, pero recomendable para mayor claridad.

Ejemplos comunes: `ui`, `auth`, `api`, `core`, `docs`, `tests`

```bash
feat(ui): agregar modo oscuro
fix(api): corregir respuesta del endpoint /users
```

---

## ✍️ Descripción

- Debe escribirse en **presente** y en **minúsculas**.  
  ✅ `feat: agregar validación de correo`  
  ❌ `feat: agregó validación de correo`
- No debe terminar con punto.  
- Sé breve y específico (máx. 72 caracteres).  

---

## 🧠 Cuerpo del mensaje (opcional)

El cuerpo se usa para detallar el **por qué** y **cómo** del cambio.  
Debe ir separado del encabezado por una línea en blanco.

Ejemplo:

```bash
fix(api): corregir error 500 al crear usuario

El error se debía a una validación incorrecta en el campo "email".
Ahora se usa una expresión regular más estricta.
```

---

## 🦶 Pie del mensaje (opcional)

Se usa para notas importantes, *breaking changes* o referencias a issues.

Ejemplo:

```bash
feat(auth): agregar soporte para inicio de sesión con Google

BREAKING CHANGE: se eliminó el campo `password` del modelo de usuario.
Closes #123
```

---

## ⚠️ Cambios importantes (*Breaking Changes*)

Cuando un cambio rompe la compatibilidad con versiones anteriores,  
debes incluir la línea:

```bash
BREAKING CHANGE: <explicación>
```

Ejemplo:

```bash
feat(api): cambiar formato de respuesta en endpoints

BREAKING CHANGE: los endpoints ahora devuelven objetos en lugar de arrays.
```

---

## 💡 Buenas prácticas

✅ Usa un formato consistente en todo el proyecto.  
✅ Escribe mensajes que expliquen **qué** cambiaste, no **cómo**.  
✅ Mantén el mensaje corto y claro.  
✅ Prefiere usar un solo idioma (español o inglés) en todos los commits.  
🚫 Evita mensajes genéricos como `update`, `changes`, o `fix stuff`.

---

## 📚 Recursos recomendados

- [Conventional Commits — Sitio oficial](https://www.conventionalcommits.org/)
- [Semantic Versioning (SemVer)](https://semver.org/)
- [Commitlint — Validador de mensajes de commit](https://commitlint.js.org/)
