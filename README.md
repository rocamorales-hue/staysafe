# Stay Safe by Christian Piña

App de seguimiento de clientes · registros de Mujeres y Hombres por separado · GitHub + Google Sheets.

## Qué incluye
- Fichas completas, estatus (activa, por vencer, vencida, congelada, archivada) y avisos de renovación.
- **Planes con precio editable** (Ajustes): Entrenamiento, Alimentación, Combo y Presencial.
- Pagos por plan, historial, **congelar plan** (viaje/lesión) y cobro por **WhatsApp con datos bancarios**.
- **Programa mensual**: rutinas y dietas por persona, mes con mes, con enlaces a videos.
- **Ejercicios**: biblioteca con enlaces de video (YouTube "no listado" o Drive).
- Fotos (4 vistas) con comparador antes/después y medidas con gráfica.
- **Enlace privado de avance** para cada persona (solo lectura, solo su información).
- **Asistente**: segunda contraseña con permisos limitados (no ve Ingresos/Ajustes, no elimina).
- Reporte de ingresos por mes y por plan.

## 1. Crear la base de datos (con el Gmail de Christian)
1. Crea un Google Sheet nuevo: **Stay Safe – Base de datos**.
2. **Extensiones → Apps Script**. Borra lo que haya y pega todo `apps-script/Code.gs`.
3. Arriba cambia `CAMBIA_ESTA_CONTRASENA` por la contraseña de Christian.
   Si habrá asistente, escribe su contraseña en `CONTRASENA_ASISTENTE` (distinta a la de Christian).
4. Elige la función **configurar** y pulsa **Ejecutar**; acepta los permisos
   (si dice "app no verificada": Configuración avanzada → Ir a proyecto).
   Crea las pestañas, los planes iniciales y una carpeta privada en Drive para las fotos.
5. **Implementar → Nueva implementación → Aplicación web**
   - Ejecutar como: **Yo** · Quién tiene acceso: **Cualquier persona** (la protege la contraseña).
6. Copia la URL que termina en `/exec`.

## 2. Conectar la app
En `config.js` pega la URL: `const API_URL = 'https://script.google.com/macros/s/…/exec';`

## 3. Publicar
1. Sube los archivos (sin la carpeta `apps-script/`) a un repositorio de GitHub.
2. **Netlify** (*Add new site → Import from Git*) o **Cloudflare Pages** (framework "None"). Gratis.
3. Cada cambio en GitHub se publica solo.

## 4. Primer uso
1. Entra con la contraseña → **Ajustes**: revisa los precios y captura teléfono, correo, Instagram
   y **datos de pago** (banco, titular, cuenta). Los datos de pago se guardan en el Sheet,
   **no** en el código ni en GitHub.
2. En el iPhone: Safari → Compartir → **Agregar a pantalla de inicio**.

## Importar clientes que ya tiene (≈40)
1. En el Sheet abre la pestaña **Importar_Mujeres** o **Importar_Hombres**.
2. Una fila por persona: nombre, telefono, ciudad, profesion, edad, estatura, peso, objetivo,
   lugar (Gym/Casa/Presencial), plan, monto, inicio y fin (fechas del último plan pagado).
3. Extensiones → Apps Script → ejecuta **importar**. Las filas importadas se marcan "SI";
   los nombres que ya existen se omiten. Después sube las fotos desde la app.

## Enlace de avance para clientes
En la ficha → **Enlace de avance**: copia o envía por WhatsApp. La persona ve solo su
programa, medidas y fotos (nunca pagos). **Generar enlace nuevo** desactiva el anterior;
archivar a la persona también lo desactiva.

## Notas
- Si cambias `Code.gs`: **Implementar → Administrar implementaciones → editar → Nueva versión**.
- Cambiar contraseñas: edita las constantes y vuelve a ejecutar `configurar`.
- Con `API_URL` vacío la app corre en modo demo (datos ficticios; contraseña `asistente` entra como asistente).
- El dominio propio se agrega después en Netlify/Cloudflare sin rehacer nada.
