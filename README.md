# Xpress El Salvador

Aplicación web de control de guías, envíos, pilotos y afiliación para **Xpress El Salvador**.

Archivo único (`index.html`) listo para alojar como sitio estático.

## Requisitos

- Navegador moderno (Chrome, Edge, Safari, Firefox)
- Proyecto Firebase (`xpress-control`) con:
  - Authentication (correo/contraseña)
  - Firestore
  - Storage
- Conexión a internet (CDN: Firebase, Leaflet, jsPDF, QRCode)

## Cómo probar en local

1. Abre la carpeta del proyecto.
2. Sirve el archivo con un servidor local (recomendado; `file://` limita cámara, GPS y PWA):

```bash
# Python
python3 -m http.server 8080

# o Node
npx serve .
```

3. Entra a: http://localhost:8080

## Subir a GitHub

```bash
cd xpress-el-salvador
git init
git add .
git commit -m "Xpress El Salvador — app de guías y afiliación"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/xpress-el-salvador.git
git push -u origin main
```

> Sustituye `TU_USUARIO` por tu usuario o organización de GitHub.

## Publicar en línea (GitHub Pages)

1. En el repositorio: **Settings → Pages**
2. Source: branch `main`, carpeta `/ (root)`
3. Guarda y espera 1–2 minutos
4. URL típica: `https://TU_USUARIO.github.io/xpress-el-salvador/`

También puedes desplegar el mismo `index.html` en Netlify, Vercel o Firebase Hosting.

### Firebase Hosting (opcional)

```bash
npm install -g firebase-tools
firebase login
firebase init hosting
# Public directory: .
# Single-page app: No
firebase deploy
```

## Roles de la app

| Rol | Uso principal |
|-----|----------------|
| Cliente | Crear guías, recolección, perfil |
| Piloto | Rutas, entregas, escaneo |
| Administrativo | Operación diaria de guías |
| Super Administrativo | Configuración, empleados, finanzas |

Desde el login también se puede:

- Solicitar **afiliación** (sin sesión)
- **Rastrear** una guía pública (`?rastreo=CODIGO`)

## Campos de afiliación (formulario público)

- Datos del comercio y contacto  
- Tipo de persona (Natural / Jurídica)  
- Banco, número de cuenta y tipo de cuenta (Ahorro / Corriente)  
- Crédito fiscal + NIT (opcional)  
- Fotos de DUI (y NIT si aplica)  
- Firma digital y aceptación de términos  

## Impresión de etiquetas

En la vista previa de impresión puedes elegir:

- **4×6 in** (estándar)
- **4×4 in**
- **4×2 in** (compacta)

Pensado para impresoras normales. Con varios bultos se imprime una etiqueta por bulto (`1/N`, `2/N`…) sobre la **misma** guía.

## Seguridad

- La configuración de Firebase del cliente está en el HTML (normal en apps web).
- La seguridad real depende de las **Firestore Security Rules**, **Storage Rules** y **Authentication**.
- No subas archivos de reglas o claves de servicio de administrador a un repo público.
- Revisa en Firebase Console que las rules no permitan lectura/escritura abierta a cualquiera.

## Versión

Ver el texto *Build* al final de la pantalla de login (ej. `2026-08-12.31`).

## Licencia

Uso interno de Xpress El Salvador. Todos los derechos reservados.
