# CLAUDE.md · repositorio `mi-web`

Reglas para Claude en este repositorio. Léelas completas antes de cambiar algo.

## Qué es este repositorio

La web de un ejecutivo o ejecutiva de isapre: **una página principal + una landing por avatar** (por ejemplo: minero, profesional independiente, mamá profesional). Cada página tiene el formulario de EOS: el lead cae directo en su bandeja del CRM.

Está conectado a Vercel. **Cada cambio que subes a GitHub se publica solo**:
- en una rama aparte → Vercel arma un **link de vista previa** (aparece en el pull request);
- cuando la dueña aprieta **Merge** → queda publicado en su dominio.

Quien lo usa no programa. Habla contigo en español, en palabras simples.

## Mis datos

> Esta sección la completa la dueña en su primera sesión. Si algo dice `[PENDIENTE]`, pregúntalo antes de usarlo; no lo inventes.

- Nombre: [PENDIENTE]
- Correo: [PENDIENTE]
- WhatsApp (solo números, con 56): [PENDIENTE]
- Dominio: [PENDIENTE] (mientras no haya, la dirección de Vercel: `https://mi-web-XXXX.vercel.app`)
- Colores y estilo: [PENDIENTE]
- Avatares (a quién le habla cada landing): [PENDIENTE]

## Estructura

```
index.html                 ← la página principal: sudominio.cl
minero/index.html          ← una landing: sudominio.cl/minero
independiente/index.html   ← otra landing: sudominio.cl/independiente
gracias/index.html         ← adonde llega la persona después del formulario
privacidad/index.html      ← política de privacidad (Ley N° 21.719)
terminos/index.html        ← términos y condiciones
imagenes/                  ← fotos y logos que usan todas las páginas
componentes/formulario-eos.html ← el formulario de EOS, tal como lo entrega EOS
vercel.json                ← no se toca
```

- **Una landing = una carpeta con su `index.html`.** El nombre de la carpeta es la dirección: minúsculas, sin tildes, sin espacios, palabras separadas con guion (`mama-profesional`, no `Mamá Profesional`).
- La principal va **en la raíz**, nunca dentro de una carpeta.
- Las imágenes van en `imagenes/` y se enlazan con ruta desde la raíz: `/imagenes/foto.jpg`.
- Los enlaces entre páginas también desde la raíz: `/gracias`, `/privacidad`, `/minero`. Nunca `gracias.html` ni `../`.
- Todo en un solo archivo por página: el CSS y el JavaScript van dentro del `index.html`. Sin frameworks, sin compilación, sin `npm`.

## El formulario de EOS — 🛑 la regla más importante

El formulario es lo que hace que la web sirva: si se rompe, los leads se pierden sin que nadie se entere.

1. **El código sale de EOS** (CRM → Formularios → copiar código) y se guarda **tal cual** en `componentes/formulario-eos.html`. Si la dueña te pega un código nuevo, reemplaza ese archivo completo.
2. En cada página que lleve formulario, se pega **ese bloque completo, sin cambiarle nada**, desde `<div id="capta"></div>` hasta el último `</script>`.
3. Lo único que puedes ajustar dentro del bloque, y solo si la dueña lo pide para esa landing, son estas líneas:
   - `TITULO`, `BAJADA`, `TEXTO_BOTON`, `TEXTO_FINAL`;
   - la lista `PREGUNTAS` (agregar, sacar o cambiar textos). **Nunca saques las preguntas con id `nombre` y `telefono`** y nunca les cambies el id.
4. **`LLAVE` no se toca nunca.** Es la que dice en qué bandeja cae el lead.
5. **`GRACIAS` es siempre la dirección completa**, con `https://` y el dominio: `https://sudominio.cl/gracias`. Nunca `gracias`, `gracias.html`, `/gracias` ni sin `https://`. Si EOS no recibe una dirección completa, la persona no llega a la página de gracias.
6. Si `LLAVE` dice `PEGA-AQUI-TU-LLAVE`, el formulario **no manda nada**: avísale a la dueña que falta pegar su código de EOS.
7. Si el diseño de la landing es oscuro, no cambies los colores del formulario: tiene fondo blanco propio a propósito.

## Lo que no se toca

- `vercel.json`, la carpeta `gracias/`, `privacidad/` y `terminos/` solo cambian si la dueña lo pide.
- No borres páginas ni carpetas sin preguntar.
- Nunca escribas contraseñas, llaves secretas ni datos de clientes (nombres, teléfonos, RUT) en archivos, commits o pull requests.
- No agregues analítica, píxeles ni servicios externos sin que la dueña lo pida.

## Cómo escribir las páginas

- Español de Chile tratando de «tú». **Nunca voseo** (nada de «tenés», «pegá», «querés»).
- **Valor primero, descripción después**: el título dice lo que la persona gana, no lo que vende la ejecutiva.
- Una landing le habla a **un solo avatar**: su dolor, su situación, su lenguaje.
- **No inventes cifras, precios, porcentajes ni testimonios.** Si hace falta un dato, pídeselo a la dueña.
- La dueña es ejecutiva de isapre: **nunca escribas que es asesora independiente** ni que compara todas las isapres.
- Toda página lleva al pie los enlaces a `/privacidad` y `/terminos`.
- Cada página tiene que verse bien en el celular (360 px de ancho): la mayoría de los leads entra desde Instagram y Facebook.

## Cómo entregar

- Trabaja siempre en una rama nueva. Nunca directo en `main`.
- Al terminar, deja el cambio listo para pull request y explícale a la dueña, en palabras simples:
  1. qué hiciste y en qué página;
  2. que abra el pull request y entre al link **«Visit Preview»** de Vercel para mirarlo;
  3. que, si le gusta, apriete **«Merge pull request»** y en un minuto está en su dominio.
- Si te pide una landing nueva, dile al final cuál va a ser la dirección: `https://sudominio.cl/nombre-de-la-carpeta`.
