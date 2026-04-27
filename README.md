Cementerio (Monorepo)

Repositorio monolítico que contiene frontend y backend para la gestión de registros de cementerio.

🚀 Requisitos
Node.js (recomendado: versión LTS)
PostgreSQL
📦 Instalación

Desde la raíz del proyecto:

npm run install:all
🗄️ Configuración de Base de Datos (PostgreSQL)
Crear el archivo de entorno:
cp backend/.env.example backend/.env
Completar las credenciales de la base de datos en backend/.env.
Ejecutar las migraciones:
npm --prefix backend run db:migrate
🧪 Desarrollo
Ejecutar frontend + backend

Desde la raíz:

npm run dev
Ejecutar por separado
Backend
cd backend
npm run dev
# o
npm run start
Frontend
cd frontend
npm run dev
🌐 Endpoints de desarrollo
Backend
Base: http://localhost:3001
Health:
/health
/api/health
/api/health/db
Frontend
http://localhost:5173
🔐 Autenticación (Email + Contraseña)

⚠️ Requiere ejecutar las migraciones:

backend/sql/005_password_auth.sql
backend/sql/006_email_verification.sql
Endpoints
Registro
POST /api/auth/register

Body:

{
  "email": "...",
  "documentId": "...",
  "phone": "...",
  "password": "...",
  "confirmPassword": "...",
  "acceptTerms": true
}
Verificación de correo
POST /api/auth/verify-email
Login
POST /api/auth/login
Usuario actual
GET /api/auth/me
🔎 Búsqueda (MVP)
GET /api/search?q=...
Requiere sesión activa.
Devuelve lista de difuntos con ubicación y estado.
📥 Carga de Datos (MVP - API)
Admin
Crear sector:
POST /api/admin/sectors
Crear tumba:
POST /api/admin/graves
Admin / Empleado
Registrar entierro:
POST /api/employee/burials
⚙️ Notas importantes

El frontend usa un proxy de desarrollo, redirigiendo /api/* hacia:

http://localhost:3001
⚠️ Error común:

Si estás dentro de backend/, no uses:

npm --prefix backend ...

Esto provocará:

ENOENT: backend/backend/package.json