# Shopping Cart
Aplicación de ejemplo que muestra un listado de productos y permite agregar artículos a un carrito de compras. El proyecto demuestra manejo del DOM, eventos y manipulación de arrays para:

- añadir productos al carrito,
- actualizar cantidades cuando se agrega el mismo producto,
- eliminar ítems individualmente,
- y vaciar el carrito por completo.

Es una base didáctica ideal para aprender interacción con el DOM y puede ampliarse con funcionalidades como persistencia en LocalStorage, cálculo de totales, o integración con una API de productos.

Para ver la demo: [Shopping Cart](https://jsproyecto1.netlify.app/)

![preview](shopping-cart-java-script.webp)

## **Características**

- Listado de productos con botón "Agregar al carrito".
- Lectura de datos del ítem seleccionado (imagen, título, precio, id).
- Mostrar en el carrito los ítems agregados.
- Actualizar la cantidad cuando se agregan ítems duplicados.
- Eliminar un ítem individual del carrito.
- Vaciar el carrito completamente.

- Persistencia del carrito usando `localStorage` para mantener los ítems entre recargas de página.
- Notificación visual y accesible al usuario cuando se agrega un ítem al carrito (mensaje temporal en pantalla).

## **Tecnologías utilizadas**

- JavaScript (DOM, eventos y manipulación de arrays).
- HTML (estructura de la página).
- CSS (estilos; incluye `skeleton`, `normalize` y `custom.css`).

## **Instalación y requisitos**

Requisitos mínimos:

- Navegador moderno (Chrome, Firefox, Safari).
- No requiere servidor ni dependencias externas para uso básico.

Pasos para ejecutar localmente:

1. Clona el repositorio o descarga los archivos.

	```bash
	git clone https://github.com/mariokarajallo/shopping-cart-java-script.git
	cd shopping-cart-java-script
	```

2. Abre `index.html` en el navegador. Para una experiencia más estable (evitar problemas con rutas de recursos), sirve el directorio con un servidor estático, por ejemplo:

	```bash
	# Python 3
	python3 -m http.server 8000

	# luego abrir http://localhost:8000
	```

## **Cómo funciona**

El comportamiento principal del carrito está implementado en `js/app.js` y sigue este flujo:

- Se usan selectores del DOM para obtener elementos clave: el listado de productos (`#lista-cursos`), el contenedor del carrito (`#carrito` y `#lista-carrito tbody`) y el botón para vaciar (`#vaciar-carrito`).
- Al hacer clic en un botón con la clase `agregar-carrito`, se recorre el DOM para extraer los datos del curso seleccionado (imagen, título, precio, id) y crear un objeto `infoCurso`.
- Los ítems se guardan en el arreglo `articulosCarrito`. Si se agrega un mismo curso (mismo `id`), se incrementa la propiedad `cantidad` en lugar de duplicar la entrada.
- El carrito se renderiza en el `tbody` creando filas (`<tr>`) con la información: imagen, título, precio, cantidad y un enlace para eliminar (`.borrar-curso` con `data-id`).
- Al hacer clic en el enlace de borrado, se filtra `articulosCarrito` para quitar el elemento por `id` y se vuelve a renderizar el HTML del carrito.
- El botón "Vaciar carrito" reinicia `articulosCarrito` a un arreglo vacío y limpia el HTML.

- Al cargar la página (`DOMContentLoaded`) el script intenta recuperar el carrito guardado en `localStorage` y lo renderiza automáticamente.
- Cada vez que se modifica el carrito se sincroniza en `localStorage` mediante `localStorage.setItem('carrito', ...)`.
- Al agregar un ítem, además de actualizar el arreglo y renderizar, se muestra una notificación temporal en pantalla (función `mostrarNotificacion`) con `role="status"` y `aria-live="polite"` para accesibilidad.

Funciones clave en `js/app.js`:

- `cargarEventListener()` — registra los event listeners principales.
- `agregarCurso(e)` — detecta clicks en "agregar" y obtiene el curso seleccionado.
- `leerDatosCurso(curso)` — construye `infoCurso`, actualiza `articulosCarrito` y llama a `carritoHTML()`.
- `carritoHTML()` — renderiza el contenido del carrito en el DOM.
- `eliminarCurso(e)` — elimina un curso por `data-id`.
- `limpiarHTML()` — limpia el contenido del `tbody` del carrito.
 - `sincronizarStorage()` — guarda `articulosCarrito` en `localStorage`.
 - `mostrarNotificacion(mensaje)` — crea una notificación temporal en pantalla cuando se agrega un ítem.

## **Estructura de archivos**


```bash
📂 shopping-cart-java-script/
├── index.html
├── README.md
├── LICENSE.md
├── css/
│   ├── custom.css
│   ├── normalize.css
│   └── skeleton.css
├── img/
└── js/
	└── app.js
```

Raíz del proyecto:

- `index.html` — vista principal con el listado y el carrito.
- `README.md` — documentación del proyecto.
- `LICENSE.md` — licencia MIT.
- `css/` — hojas de estilo (`custom.css`, `normalize.css`, `skeleton.css`).
- `img/` — imágenes usadas en la demo.
- `js/app.js` — lógica del carrito y manejo del DOM.



## **Contribuciones**

Si quieres contribuir:

1. Haz un fork del repositorio.
2. Crea una rama con tu mejora: `git checkout -b feature/nombre-feature`.
3. Haz tus cambios, prueba y commitea: `git commit -m "Descripción"`.
4. Envía un Pull Request describiendo tus cambios.

Sugerencias de mejoras posibles: persistencia del carrito en LocalStorage, integración con una API para productos, o tests automatizados.

## **Créditos**

- **Juan Pablo De la Torre Valdez** - Instructor y autor del contenido del curso - [Codigo Con Juan](https://codigoconjuan.com/).
- **Mario Karajallo** - Implementación del proyecto y mantenimiento - [Mario Karajallo](https://karajallo.com).

## **Licencia**

Este proyecto está bajo la licencia MIT. Véase `LICENSE.md` para más detalles.

---

⌨️ con ❤️ por [Mario Karajallo](https://karajallo.com)