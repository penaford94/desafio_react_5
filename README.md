# 🍕 Pizzería Mamma Mía — Hito 5

En este proyecto implementé la navegación de Pizzería Mamma Mía utilizando React, Vite y React Router. Organicé las páginas y configuré sus rutas para navegar entre ellas sin recargar completamente la aplicación.

Mantuve los formularios de Login y Register, el carrito y la barra de navegación siguiendo lo trabajado en el curso. También incorporé las páginas Profile y NotFound.

## Tecnologías utilizadas

- JavaScript y JSX.
- React.
- Vite.
- React Router DOM 6.
- Bootstrap 5.
- React Bootstrap.
- ESLint.

Las dependencias están declaradas en `package.json` y sus versiones resueltas se encuentran en `package-lock.json`.

## Instalación y ejecución

Para ejecutar el proyecto necesito Node.js y npm instalados.

Después de clonar el repositorio o descomprimir el proyecto, abro una terminal en la carpeta que contiene `package.json`.

Instalo las dependencias:

```bash
npm install
```

Inicio el servidor de desarrollo:

```bash
npm run dev
```

Luego abro la dirección que indica Vite en la terminal.

### Backend

Las páginas Home y Pizza consumen una API local:

| Página | Endpoint |
| --- | --- |
| Home | `http://localhost:5000/api/pizzas` |
| Pizza | `http://localhost:5000/api/pizzas/p001` |

Para cargar los datos necesito ejecutar por separado el backend proporcionado en el curso, siguiendo sus instrucciones.

El backend no está incluido en este proyecto. Si no está disponible, las páginas muestran un mensaje de error de carga.

## Organización del proyecto

| Archivo o carpeta | Responsabilidad |
| --- | --- |
| `src/main.jsx` | Inicio de React, BrowserRouter y estilos de Bootstrap |
| `src/App.jsx` | Definición de rutas y navegación |
| `src/pages/` | Páginas de la aplicación |
| `src/components/Navigation.jsx` | Barra de navegación |
| `src/components/Header.jsx` | Encabezado de Home |
| `src/components/CardPizza.jsx` | Tarjetas de pizzas |
| `src/utils/pizza.js` | Datos locales y carrito inicial |
| `src/utils/formatCurrency.js` | Formato de importes |
| `src/assets/` | Imágenes y recursos |
| `src/index.css` y `src/App.css` | Estilos propios |

Conservé los componentes AccessForm y Footer, aunque actualmente no los renderizo en la aplicación. Login y Register utilizan sus propios formularios.

## Rutas implementadas

| Ruta | Página |
| --- | --- |
| `/` | Home |
| `/register` | Register |
| `/login` | Login |
| `/cart` | Cart |
| `/pizza/p001` | Pizza |
| `/profile` | Profile |
| `/404` | NotFound |
| `*` | NotFound para rutas inexistentes |

Configuré BrowserRouter en `main.jsx` para proporcionar el contexto de navegación.

En `App.jsx` utilicé Routes y Route para relacionar cada URL con su página. Dejé Navigation fuera de Routes para mantener el menú visible al cambiar de vista.

## Funcionalidades implementadas

### Barra de navegación

Construí la barra utilizando Navbar y Container de React Bootstrap.

Utilicé Link para navegar entre las páginas sin recargar completamente el documento. El enlace NotFound apunta a `/404`.

También agregué el total en la barra de navegación mediante un enlace con destino `/cart`.

### Catálogo y detalle

En Home obtengo el catálogo desde la API y muestro las pizzas mediante CardPizza.

En Pizza consulto el detalle de la pizza `p001`.

Utilicé:

- `useEffect` para realizar las consultas.
- `useState` para administrar datos, carga y errores.
- `fetch` para obtener la información.
- AbortController para cancelar solicitudes cuando se limpia el efecto.

### Login y Register

Implementé formularios controlados con `useState`.

Evité la recarga al enviar los formularios mediante `event.preventDefault()`.

Las validaciones comprueban:

- Que los campos no estén vacíos.
- Que la contraseña tenga al menos seis caracteres.
- Que las contraseñas coincidan en Register.

Muestro mensajes de error o éxito según el resultado.

Los formularios todavía simulan el inicio de sesión y el registro: no envían credenciales al backend ni crean una sesión real.

Actualmente uso `noValidate` y las comprobaciones manuales no incluyen la validación del formato del email.

### Carrito

Inicialicé el carrito con los datos de `pizzaCart`.

Implementé controles para aumentar y disminuir las cantidades. Cuando la cantidad llega a cero, elimino el producto del carrito.

Calculo el total sumando el precio multiplicado por la cantidad de cada producto. Utilizo `formatCurrency` para presentar los importes con formato regional chileno.

El estado del carrito permanece dentro de Cart. Al salir de esta página y volver a entrar, se restaura el carrito inicial.

### Profile

Agregué una página de perfil con un email de ejemplo y un botón para cerrar sesión.

Ambos son estáticos, como permite la consigna de este hito.

### NotFound

Creé una página de error con un mensaje personalizado y un enlace para volver al inicio.

Configuré dos rutas para esta vista:

- `/404`, para acceder directamente.
- `*`, para mostrarla cuando ninguna ruta coincide.

## Requerimientos del hito implementados

- Instalación y configuración de React Router.
- Organización de Home, Register, Login, Cart y Pizza dentro de `pages`.
- Configuración de las siete rutas solicitadas.
- Página NotFound para rutas inexistentes.
- Enlace desde NotFound hacia el inicio.
- Perfil con email y botón de cierre de sesión.
- Barra de navegación con Link.
- Enlace del total hacia `/cart`.

## Alcance actual

El proyecto se enfoca en el enrutamiento solicitado para este hito.

Para futuras etapas queda:

- Implementar autenticación real.
- Conectar los botones Ver más y Añadir de CardPizza.
- Conectar Añadir del detalle con el carrito.
- Implementar el proceso de pago.
- Compartir y persistir el estado del carrito.
- Verificar que el total de la navegación se actualice al modificar cantidades.

Los botones Añadir, Pagar y Cerrar sesión todavía no ejecutan esas operaciones.

## Comandos disponibles

| Comando | Función |
| --- | --- |
| `npm run dev` | Ejecutar el servidor de desarrollo |
| `npm run lint` | Revisar el código con ESLint |
| `npm run build` | Generar la compilación de producción |
| `npm run preview` | Revisar localmente una compilación generada |

## Comprobaciones antes de entregar

1. Recorrer todas las rutas desde el navegador.
2. Comprobar que el menú permanece visible.
3. Verificar que el enlace del total lleva a `/cart`.
4. Verificar que NotFound lleva a `/404`.
5. Visitar una ruta inexistente y volver al inicio.
6. Ejecutar el backend para comprobar Home y Pizza.
7. Probar las validaciones de Login y Register.
8. Aumentar y disminuir cantidades en el carrito.
9. Ejecutar `npm run lint` y `npm run build`.

## Lo que practiqué

Con este proyecto practiqué la organización de páginas y componentes, la configuración de rutas, la navegación con Link, los formularios controlados, el consumo de una API y la actualización del estado en React.

## ¿Qué me falta?

1. Necesito darle una correcta utilización al componente Pizza.jsx para que sirva al darle click a Ver más dentro de la página Home y entregue el valor por cada pizza considerando su valor, descripción e ingregientes, en la barra de navegación no se ve natural para el usuario.
2. Necesito darle funcionalidad e interactividad al botón de total del carrito y que sea sensible a la interacción con las elecciones de la página, que interactue con el botón de Añadir de Home.