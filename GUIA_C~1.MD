# Guía de configuración — Registro Centro

Seguí estos 3 pasos una sola vez para dejar la app funcionando.

---

## PASO 1 — Crear cuenta en GitHub (5 minutos)

1. Entrá a **https://github.com** y hacé clic en **Sign up**
2. Ingresá tu email, una contraseña y un nombre de usuario
3. Confirmá el email que te mandan
4. Una vez dentro, hacé clic en el **+** arriba a la derecha → **New repository**
5. Nombre del repositorio: `registro-centro`
6. Marcá **Public**
7. Hacé clic en **Create repository**

---

## PASO 2 — Subir los archivos de la app

1. En la página del repositorio que acabás de crear, hacé clic en **uploading an existing file**
2. Arrastrá estos 4 archivos (están en tu carpeta de descargas/outputs):
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - Los íconos `icon-192.png` e `icon-512.png` *(ver nota abajo)*
3. Hacé clic en **Commit changes**

> **Íconos**: Para generarlos gratis, entrá a https://favicon.io/favicon-generator/
> Escribí un texto (ej. "RC"), elegí fondo azul (#185FA5) y texto blanco.
> Descargá y usá `android-chrome-192x192.png` y `android-chrome-512x512.png`,
> renombrándolos a `icon-192.png` y `icon-512.png`.

**Activar GitHub Pages:**
1. En el repositorio, entrá a **Settings** → **Pages** (menú izquierdo)
2. En **Source**, seleccioná la rama **main** y la carpeta **/ (root)**
3. Hacé clic en **Save**
4. En unos minutos, aparecerá la URL de tu app:
   `https://TU_USUARIO.github.io/registro-centro/`
   **Guardá esta URL** — la vas a necesitar en el Paso 3.

---

## PASO 3 — Crear las credenciales de Google (10 minutos)

Esto le dice a Google que la app tiene permiso para leer y escribir en tu planilla.

1. Entrá a **https://console.cloud.google.com**
   (usá la misma cuenta de Google que tiene acceso a la planilla)

2. **Crear un proyecto:**
   - Hacé clic en el selector de proyectos arriba → **Nuevo proyecto**
   - Nombre: `Registro Centro` → **Crear**

3. **Habilitar la API de Sheets:**
   - Menú izquierdo → **APIs y servicios** → **Biblioteca**
   - Buscá `Google Sheets API` → **Habilitar**

4. **Configurar pantalla de consentimiento:**
   - Menú izquierdo → **APIs y servicios** → **Pantalla de consentimiento de OAuth**
   - Tipo: **Externo** → **Crear**
   - Nombre de la app: `Registro Centro`
   - Email de asistencia: tu email
   - Hacé clic en **Guardar y continuar** (3 veces, sin tocar nada más)
   - En **Usuarios de prueba**, agregá los emails de todas las personas que van a usar la app
   - Hacé clic en **Guardar y continuar** → **Volver al panel**

5. **Crear credencial OAuth:**
   - Menú izquierdo → **APIs y servicios** → **Credenciales**
   - **+ Crear credenciales** → **ID de cliente de OAuth**
   - Tipo: **Aplicación web**
   - Nombre: `Registro Centro`
   - En **Orígenes de JavaScript autorizados**, hacé clic en **+ Agregar URI**
     y pegá tu URL: `https://TU_USUARIO.github.io`
   - Hacé clic en **Crear**
   - Copiá el **ID de cliente** (termina en `.apps.googleusercontent.com`)

6. **Pegarlo en la app:**
   - Abrí el archivo `index.html` en el Bloc de notas
   - Buscá la línea: `const CLIENT_ID = 'TU_GOOGLE_CLIENT_ID.apps.googleusercontent.com';`
   - Reemplazá `TU_GOOGLE_CLIENT_ID.apps.googleusercontent.com` por el ID que copiaste
   - Guardá el archivo
   - Volvé a subirlo a GitHub (mismos pasos del Paso 2)

---

## PASO 4 — Instalar en el celular Android

1. Abrí **Chrome** en tu Android
2. Entrá a la URL de tu app: `https://TU_USUARIO.github.io/registro-centro/`
3. Chrome mostrará un banner que dice **"Agregar a la pantalla de inicio"** → tocalo
   (si no aparece, tocá los 3 puntos arriba a la derecha → **Instalar aplicación**)
4. La app queda como ícono en tu pantalla, igual que cualquier app

---

## Agregar o quitar usuarios autorizados

Para que otra persona pueda acceder:
1. Entrá a Google Cloud Console → tu proyecto → **APIs y servicios** → **Pantalla de consentimiento**
2. Hacé clic en **Usuarios de prueba** → **+ Agregar usuarios**
3. Ingresá el email de la persona → **Guardar**

---

## Planilla de Google Sheets vinculada

La app escribe directamente en:
`https://docs.google.com/spreadsheets/d/1zw1sza3-YfCYyNcf6bMrcYvYtgNfFe5crUvLa4jFUu8`

Cada ingreso agrega una fila nueva. Cada egreso actualiza la fila correspondiente
con la fecha de egreso, el motivo y los días internados.
