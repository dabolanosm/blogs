# 📝 Blogs — Conspiraciones

Aplicación web de blog construida con **Django**, que permite crear, leer, editar y eliminar publicaciones (CRUD completo). El proyecto está tematizado como un blog de "conspiraciones", con una interfaz simple usando Bootstrap 4.

## ✨ Características

- 📃 Listado de publicaciones en la página principal
- 🔍 Vista de detalle para cada publicación
- ➕ Crear nuevas publicaciones
- ✏️ Editar publicaciones existentes
- 🗑️ Eliminar publicaciones (con confirmación)
- 🔐 Panel de administración de Django (`/admin/`)
- 🎨 Interfaz con Bootstrap 4, jQuery y Popper.js

## 🛠️ Tecnologías

| Tecnología | Versión |
|---|---|
| Python | 3.10.4 |
| Django | 4.0.4 |
| Base de datos | SQLite3 |
| Frontend | Bootstrap 4.4.1, jQuery 3.4.1, Popper.js 1.16.0 |

## 📂 Estructura del proyecto

> ⚠️ **Nota importante:** este repositorio incluye, por error, el entorno virtual de Python completo (`Lib/site-packages` y los ejecutables dentro de `Scripts/`). El **código real del proyecto Django** vive dentro de `Scripts/blog/`. Se recomienda en el futuro agregar un `.gitignore` que excluya el venv y mover el proyecto a la raíz del repositorio.

```
blogs/
├── Lib/site-packages/          # Entorno virtual (venv) — no es código del proyecto
├── Scripts/
│   ├── blog/                    # 👉 Proyecto Django real
│   │   ├── blog/                  # Configuración del proyecto
│   │   │   ├── settings.py
│   │   │   ├── urls.py
│   │   │   ├── wsgi.py
│   │   │   └── asgi.py
│   │   ├── theblog/                # App principal del blog
│   │   │   ├── models.py             # Modelo Post
│   │   │   ├── views.py              # Vistas CRUD (ListView, DetailView, CreateView, UpdateView, DeleteView)
│   │   │   ├── forms.py              # PostForm y EditForm
│   │   │   ├── urls.py               # Rutas de la app
│   │   │   ├── admin.py              # Registro en el admin
│   │   │   └── templates/            # Plantillas HTML (base, home, detalle, formularios)
│   │   ├── db.sqlite3               # Base de datos SQLite
│   │   └── manage.py
│   ├── python.exe, pip.exe, activate, ...  # Ejecutables del venv (Windows)
├── pyvenv.cfg
└── README.md
```

## 🗄️ Modelo de datos

El modelo principal es `Post` (`theblog/models.py`):

| Campo | Tipo |
|---|---|
| `title` | CharField (máx. 255) |
| `title_tag` | CharField (máx. 255) |
| `author` | ForeignKey a `User` |
| `body` | TextField |

## 🗺️ Rutas principales

| Ruta | Vista | Nombre de la URL |
|---|---|---|
| `/` | `HomeView` (listado) | `home` |
| `/article/<id>` | `ArticleDetailView` | `article-detail` |
| `/add_post/` | `AddPostView` | `add_post` |
| `/article/edit/<id>` | `UpdatePostView` | `update_post` |
| `/article/<id>/remove` | `DeletePostView` | `delete_post` |
| `/admin/` | Panel de administración de Django | — |

## 🚀 Instalación y uso

> El proyecto fue generado originalmente con un venv de Windows con rutas específicas de esa máquina, así que se recomienda crear un entorno virtual propio en lugar de usar el que está commiteado.

### 1. Clonar el repositorio

```bash
git clone https://github.com/dabolanosm/blogs.git
cd blogs/Scripts/blog
```

### 2. Crear y activar un entorno virtual nuevo

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

### 3. Instalar dependencias

```bash
pip install django==4.0.4
```

### 4. Aplicar migraciones

```bash
python manage.py migrate
```

### 5. Crear un superusuario (opcional, para acceder al admin)

```bash
python manage.py createsuperuser
```

### 6. Levantar el servidor de desarrollo

```bash
python manage.py runserver
```

### 7. Abrir la aplicación

- App: [http://127.0.0.1:8000/](http://127.0.0.1:8000/)
- Admin: [http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)

## 📌 Notas y mejoras sugeridas

- Agregar un archivo `.gitignore` para excluir el entorno virtual (`Lib/`, `Scripts/*.exe`, `venv/`, `__pycache__/`, `db.sqlite3`).
- Mover el proyecto Django (`Scripts/blog/`) a la raíz del repositorio para simplificar la estructura.
- Agregar un archivo `requirements.txt` con las dependencias del proyecto.
- Definir una licencia para el repositorio (actualmente no tiene ninguna especificada).

## 👤 Autor

[dabolanosm](https://github.com/dabolanosm)

## 📄 Licencia

No.
