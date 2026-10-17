# Nuestra boda

Sitio privado para planear la boda a distancia: tareas, invitados, proveedores, ideas y preguntas, cronograma del día, dos relojes (uno por ciudad), cuenta regresiva y el botón de abrazos.

Es un solo archivo, `index.html`. Funciona en GitHub Pages sin servidor.

## 1. Publicarlo en GitHub Pages (10 minutos)

1. En GitHub, crea un repositorio nuevo, por ejemplo `boda`.
2. Sube `index.html`, `firestore.rules` y este `README.md`.
3. En el repositorio: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, rama `main`, carpeta `/ (root)`. Guarda.
4. En uno o dos minutos el sitio queda en `https://TU-USUARIO.github.io/boda/`.

Sin el paso 2 de abajo, cada uno ve solo lo que guarda en su propio navegador.

## 2. Que los dos vean lo mismo (Firebase, gratis)

GitHub Pages solo sirve archivos; para compartir los datos en tiempo real se usa Firestore, con el plan gratuito de Firebase.

1. Entra a <https://console.firebase.google.com> y crea un proyecto (puedes desactivar Analytics).
2. **Build → Authentication → Get started → Sign-in method → Google → Enable.**
3. En **Authentication → Settings → Authorized domains**, añade `TU-USUARIO.github.io`.
4. **Build → Firestore Database → Create database** (modo producción, región cercana, por ejemplo `northamerica-northeast1`, Montreal).
5. En la pestaña **Rules** de Firestore, pega el contenido de `firestore.rules` con sus dos correos de Google, y publica.
6. **Project settings (engranaje) → General → Your apps → Web (`</>`)**, registra la app y copia el objeto `firebaseConfig`.
7. En `index.html`, busca `const FIREBASE_CONFIG = null;` y reemplázalo:

```js
const FIREBASE_CONFIG = {
  apiKey: "...",
  authDomain: "...",
  projectId: "...",
  storageBucket: "...",
  messagingSenderId: "...",
  appId: "..."
};
```

8. Sube el cambio a GitHub. Al abrir el sitio aparece "Iniciar sesión para sincronizar"; cada uno entra con su cuenta de Google.

La clave `apiKey` de Firebase no es secreta: lo que protege los datos son las reglas del paso 5, que solo dejan entrar a sus dos correos.

## Cómo se usa

- **Soy …** (arriba): cada uno elige quién es en su teléfono. Así se marca quién hizo cada cosa.
- **Ajustes**: nombres, ciudades, zonas horarias, fecha y lugar.
- **Borrar ejemplos**: quita los invitados, proveedores, ideas y horarios de ejemplo.
- **Enviar un abrazo**: la otra persona lo ve al abrir el sitio.
- **ES · EN**: cambia el idioma de la interfaz.

Si los dos editan exactamente al mismo segundo, gana el último cambio guardado.

## Ideas para después

- Fotos en el muro de ideas (Firebase Storage).
- Página pública para invitados con RSVP, como en [rampatra/wedding-website](https://github.com/rampatra/wedding-website), que guarda las respuestas en Google Sheets.
- Recordatorios por correo de tareas que se acercan.
