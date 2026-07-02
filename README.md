# LibriSphere — Backend (Laravel API)

REST API server for the LibriSphere digital library system, built with Laravel 11 and PostgreSQL.

---

## Requirements

| Tool | Version |
|------|---------|
| PHP | 8.2 or higher |
| Composer | 2.x |
| PostgreSQL | 14 or higher |
| Node.js | 18 or higher (for Vite assets) |

---

## Step-by-Step Setup

### 1. Install PHP dependencies

```bash
cd Library_System_Backend
composer install
```

### 2. Create the environment file

```bash
copy .env.example .env
```

### 3. Configure the `.env` file

Open `.env` and update these values to match your PostgreSQL setup:

```env
APP_NAME=LibriSphere
APP_URL=http://127.0.0.1:8000

DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=Library_System
DB_USERNAME=postgres
DB_PASSWORD=your_postgres_password
```

### 4. Generate the application key

```bash
php artisan key:generate
```

### 5. Run database migrations

```bash
php artisan migrate
```

### 6. Link storage (for file uploads and cover photos)

```bash
php artisan storage:link
```

### 7. Start the development server

```bash
php artisan serve
```

The API will be available at: **http://127.0.0.1:8000**

---

## Key API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/admin/login` | Admin login |
| POST | `/api/UserRegister` | Register a new member |
| GET | `/api/Memberships/show` | List membership plans |
| GET | `/api/getResource` | List all resources |
| GET | `/api/resource/search` | Search resources |
| GET | `/api/resource/{id}` | Get resource details |

All other endpoints require a Bearer token from login (`auth:sanctum` middleware).

---

## Storage

Book cover photos and uploaded files are stored in:
```
storage/app/public/
```

The library knowledge base document for the AI chatbot is at:
```
storage/app/AboutLibrary.txt
```

---

## Troubleshooting

**`php artisan migrate` fails** — Check that PostgreSQL is running and the `DB_*` values in `.env` are correct.

**Storage files not accessible** — Run `php artisan storage:link` to create the symlink from `public/storage` to `storage/app/public`.

**500 errors** — Check `storage/logs/laravel.log` for details.
