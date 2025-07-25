# 🔧 Buenas Prácticas con Git y GitKraken

Este documento resume las buenas prácticas para usar **Git** de forma eficiente, especialmente con la interfaz visual de **GitKraken**, ideal para estudiantes y equipos de desarrollo.

---

## 🧩 1. ¿Qué es GitKraken?

GitKraken es una interfaz visual para Git que permite:
- Ver ramas y commits gráficamente
- Hacer cambios sin usar la terminal
- Colaborar con otros usando GitHub, GitLab o Bitbucket

---

## ✅ 2. Buenas prácticas generales

### 2.1 Crea un repositorio desde el inicio
- Inicia tu proyecto con control de versiones.
- Crea el repositorio local con GitKraken y conéctalo a GitHub si vas a compartir.

### 2.2 Haz commits frecuentes y con sentido
- No esperes hasta el final para hacer un solo commit grande.
- Cada commit debe representar un avance claro.

```bash
✔️ Bien: "Agregada función de ataque por turnos"
❌ Mal: "Cambios"
```

### 2.3 Escribe mensajes de commit claros
- Usa verbos en infinitivo: agregar, mejorar, corregir
- Describe qué hiciste y por qué (si es necesario)

### 2.4 Organiza tu repositorio
- Usa carpetas claras: `src/`, `assets/`, `docs/`
- Agrega un `.gitignore` que excluya archivos temporales y binarios

---

## 🌿 3. Uso de ramas

- Usa ramas para nuevas funcionalidades o experimentos.
- No trabajes directamente en `main`.

```bash
rama: puntuacion-juego
rama: ajustes-menu
```

### 3.1 ¿Cómo hacerlo en GitKraken?
- Haz clic derecho en `main` y selecciona "New branch".
- Trabaja en esa rama, haz tus commits.
- Haz merge cuando termines y verifiques que funciona.

---

## 🔄 4. Sincroniza con frecuencia

- Usa el botón "Push" para subir tus cambios a GitHub.
- Usa "Pull" para traer cambios nuevos si trabajas en equipo.

---

## 📄 5. Documenta tu repositorio

Incluye al menos:
- `README.md` con descripción del proyecto
- Capturas de pantalla o gifs si es posible
- Autores y fecha

---

## 🛡️ 6. Evita errores comunes

| Error | Cómo evitarlo |
|-------|---------------|
| Trabajar sin commits | Haz commits pequeños regularmente |
| Conflictos al hacer merge | Sincroniza y comunica con tu equipo |
| Subir binarios o temporales | Usa un buen `.gitignore` |

---

¿Deseas que lo convierta ahora en un archivo `.md`?