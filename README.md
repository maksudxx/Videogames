# 🎮 Videogames App (Full Stack) — v1.0

![Videogames App Hero](https://capsule-render.vercel.app/api?type=waving&color=timeGradient&height=250&section=header&text=Videogames%20App&fontSize=90&fontAlignY=38&desc=Explora,%20crea%20y%20gestiona%20tus%20videojuegos%20favoritos&descAlignY=51&descAlign=62)

Aplicación **Full Stack** desarrollada con fines educativos y un diseño visual extremadamente cuidado. 
La plataforma permite explorar una amplia biblioteca de videojuegos consumiendo la API de **RAWG.io**, y posibilita que los usuarios registrados creen y gestionen sus propios videojuegos mediante una base de datos propia.

Con una interfaz modernizada, fluida y con **Glassmorphism**, esta aplicación ofrece un acabado visual *premium*, 100% responsivo, con modo oscuro y paleta de colores inmersiva.

---

## ✨ Características Principales

- **Exploración de Videojuegos:** Visualización de cientos de juegos obtenidos de RAWG API con datos precisos (rating, plataformas, géneros, lanzamiento).
- **Sistema de Búsqueda y Filtrado Avanzado:** Búsqueda dinámica por nombre de videojuego. Filtros combinados por Género, Origen (API/BD) y Plataforma.
- **Creación de Títulos Propios:** Formulario controlado para agregar juegos a tu propia base de datos, con carga interactiva de imágenes mediante **Cloudinary**.
- **Autenticación y Sesión:** Sistema de Registro y Login seguro a nivel base de datos, utilizando **JWT (JSON Web Token)** y hasheo de contraseñas.
- **Diseño Moderno (Glassmorphism):** UI avanzada con efectos translúcidos (efecto cristal), fondos dinámicos, sombras suaves, bordes redondeados y un UX adaptable tanto a dispositivos móviles como de escritorio.
- **Manejo del Estado Global:** Arquitectura moderna con **Redux Toolkit** (Slices) y **Redux Thunk** para peticiones asíncronas limpias y escalables.

---

## 🛠️ Tecnologías y Herramientas

### 🎨 Frontend (Client)
- **React 18 & Vite:** Framework y bundler de altísimo rendimiento.
- **Redux Toolkit & React-Redux:** Manejo de estado global asíncrono robusto.
- **Styled-Components & Material UI:** Sistema de diseño responsivo de primer nivel.
- **React Router Dom (v5):** Navegación fluida tipo SPA sin recarga de página.
- **React Paginate:** Navegación por páginas para grandes volúmenes de videojuegos.
- **Axios & React Toastify:** Peticiones HTTP eficientes a la API y notificaciones emergentes amigables al usuario (Ej: éxito y errores).
- **Cloudinary React:** Componentes específicos para optimización de imágenes en el lado cliente.

### ⚙️ Backend (API)
- **Node.js & Express:** Entorno de ejecución y framework ágil para desarrollo de API RESTful.
- **Sequelize ORM:** Interacción con base de datos orientada a objetos (uso de modelos).
- **PostgreSQL:** Sistema de base de datos relacional para datos persistentes.
- **Bcrypt & JSON Web Token:** Hasheo y verificación de credenciales y autorización por rutas protegidas.
- **Morgan, Body-Parser, CORS & Dotenv:** Middlewares para validaciones de seguridad, logs de la aplicación y variables de entorno (`.env`).

---

## 🚀 Instalación y Ejecución Local

### 1. Clonar el repositorio
```bash
git clone <url-del-repositorio>
cd Videogames
```

### 2. Configurar el Backend (Carpeta `api`)
Abre una terminal y dirígete a la carpeta `api`:
```bash
cd api
npm install
```
Crea un archivo `.env` en la raíz de la carpeta `api` basándote en el archivo de plantilla `.env.template`:
```env
DB_USER=TU_USUARIO
DB_PASSWORD=TU_PASSWORD
DB_HOST=localhost
DATABASE=videogames
PORT=3001
API_KEY=TU_API_KEY_RAWG
JWT_SECRET=TU_SECRET_JWT
```
Ejecuta el servidor en modo desarrollo:
```bash
npm run dev
```

### 3. Configurar el Frontend (Carpeta `client`)
Abre otra terminal y dirígete a la carpeta `client`:
```bash
cd client
npm install
```
Asegúrate de configurar `.env` si es necesario (ej: `VITE_API_URL=http://localhost:3001` si deseas usar variables en desarrollo o producción). 
Ejecuta la vista principal del frontend:
```bash
npm run dev
```
Accede desde tu navegador al puerto proporcionado por Vite (usualmente `http://localhost:5173`).

---

## 📡 Endpoints de la API REST

Base del proyecto desplegado/local (Ej. `http://localhost:3001`).

### 🎮 Videojuegos
- `GET /videogames`: Obtiene listado paginado (desde API externa + BD).
- `GET /videogames?name=...`: Búsqueda específica que filtre las coincidencias de nombres.
- `GET /videogame/:id`: Obtiene datos técnicos del juego especificado (rating, release date).
- `POST /videogame`: Crea un nuevo juego (Requiere JWT válido).
- `PUT /videogame/:id`: Modifica un videojuego creado (Requiere JWT válido).
- `DELETE /videogame/:id`: Elimina un escenario creado en BD.

### 🏷️ Datos Relacionados
- `GET /genres`: Array completo de géneros listos (precargados de RAWG API).
- `GET /platforms`: Devuelve todas las plataformas de los videojuegos.
- `GET /tags`: Devuelve tags extras asociados.

### 👤 Usuarios y Autenticación (Seguridad)
- `POST /register`: Da de alta a un usuario nuevo. Hashea contraseñas y graba a la BD (Email, Password, Username).
- `POST /login`: Validación de credenciales. Regresa JWT en respuesta si es exitoso.
- `GET /is-verify`: (Require Token) Valida y reanuda sesión frontend activa.
- `GET /user`: Obtiene los datos del perfil actual (Requiere Token).

---

## 📱 Secciones del Frontend

- **`/` (Explorador Home):** Vista principal con tarjetas (`Cards`) 100% responsivas, barra de búsqueda lateral/modal para filtros robustos.
- **`/videogame/:id` (Vista Detalle):** Ruta dedicada a desplegar información puntual del juego de forma inmersiva sin sobrecargar de componentes.
- **`/newGame` (Creación Formulario):** Solo puedes acceder logueado. Componente donde ingresas datos, previsualizas imágenes en vivo y envías los datos mediante Axios al backend.
- **`/login` & `/register` (Acceso):** Vistas donde registras y logueas tu cuenta en la red y evitas rutas caídas, permitiendo gestionar tokens internamente en localStorage/Redux state.
- **`/about` (Desarrollo):** Información del proyecto, link, CV y metas del desarrollador.

---

## 📝 Comentarios Finales

Este proyecto fue desarrollado y refactorizado profundamente por **Facundo Maksud**.  
Se puso un especial énfasis en la **limpieza del código**, **rendimiento y experiencia del usuario (Responsive Design & Glassmorphism)** integrados en una SPA veloz y elegante.

🔗 **Link del Deploy (Ejemplo):** [https://videogames-brown.vercel.app/](https://videogames-brown.vercel.app/)

Cualquier feedback es bienvenido. ¡Gracias por explorar la App! 🙌
