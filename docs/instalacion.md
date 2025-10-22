# 🛠 Guía de Instalación - CotareloManage

Manual completo para instalar y configurar el sistema educativo.

---

## ⚙️ **Requisitos del Sistema**

| Componente | Versión Mínima | Recomendada | Estado |
|-------------|----------------|--------------|--------|
| Node.js | 16.x | 18.x LTS | ✅ |
| npm | 8.x | 9.x | ✅ |
| MongoDB | 5.0 | 6.0+ | ⚠️ |
| Redis | 6.x | 7.x | 🔄 |

---

## 💻 **Sistemas Operativos Soportados**

✅ Windows 10/11  
✅ macOS Monterey+  
✅ Ubuntu 20.04 LTS+  
✅ CentOS 8+

---

## 🎯 **Métodos de Instalación**

### 🔹 Opción 1: Instalación Automática (Recomendada)

```bash
curl -fsSL https://install.CotareloManage.es/setup.sh | bash
# o usando wget
wget -qO- https://install.CotareloManage.es/setup.sh | bash
```

---

### 🔹 Opción 2: Instalación Manual

**Paso 1: Clonar el Repositorio**
```bash
git clone https://github.com/CotareloManage/sistema-escolar.git
cd sistema-escolar
```

**Paso 2: Configurar Variables de Entorno**
Crea un archivo `.env` con la siguiente configuración:

```bash
# Base de datos
DATABASE_URL=mongodb://localhost:27017/CotareloManage
REDIS_URL=redis://localhost:6379

# Autenticación
JWT_SECRET=tu_clave_super_secreta_aqui_2024
JWT_EXPIRY=24h

# Email (opcional)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=tu-email@gmail.com
SMTP_PASS=tu-contraseña-app
```

**Paso 3: Instalar Dependencias**
```bash
npm install
cd client && npm install && cd ..
```

---

## 🐳 **Instalación con Docker**

Archivo `docker-compose.yml`:

```yaml
version: '3.8'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
    depends_on:
      - mongodb
      - redis
  
  mongodb:
    image: mongo:6.0
    ports:
      - "27017:27017"
    volumes:
      - mongodb_data:/data/db
      
  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"

volumes:
  mongodb_data:
```

Ejecutar con:
```bash
docker-compose up -d
```

---

## ✅ **Checklist Post-Instalación**

### 1️⃣ Servicios Básicos
- [x] Base de datos conectada  
- [x] Redis funcionando  
- [x] Servidor web iniciado  
- [x] SSL configurado  

### 2️⃣ Funcionalidades Core
- [x] Login de usuarios  
- [x] Dashboard principal  
- [x] Módulo de calificaciones  
- [x] Sistema de notificaciones  

---

## 🚨 **Solución de Problemas Comunes**

**Error:** `Cannot connect to MongoDB`  
**Causa:** MongoDB no está iniciado o la URL de conexión es incorrecta.  

**Soluciones:**
1. Verificar que MongoDB esté ejecutándose:
   ```bash
   sudo systemctl status mongodb
   ```
2. Revisar la variable `DATABASE_URL` en el archivo `.env`  
3. Comprobar permisos de red:
   ```bash
   telnet localhost 27017
   ```

---

## 🔄 **Actualizaciones**

### Actualización Automática
```bash
npm run enable-auto-update
# para desactivar:
npm run disable-auto-update
```

### Actualización Manual
```bash
npm run backup
git pull origin main
npm install
npm run migrate
npm run restart
```

---

## 🏁 **Siguientes Pasos**

1. Configura tu primer usuario administrador  
2. Personaliza la configuración del centro educativo  
3. Importa datos existentes (si los hay)  
4. Capacita al personal en el uso del sistema  

💡 **Tip:** Mantén siempre actualizada la documentación y realiza backups regulares.  

📧 Soporte: [support@CotareloManage.es](mailto:support@CotareloManage.es)  

✅ *Instalación completada exitosamente.*
