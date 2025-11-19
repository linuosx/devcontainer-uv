
# 1. devcontainer-uv

Proyecto de estructura para crear un devcontainer de Python con la herramienta **uv**.

## 1.2. Características

- **Devcontainer preconfigurado** para desarrollo consistente
- **Gestor de paquetes uv** para instalación rápida de dependencias
- **Sincronización automática** de paquetes si existe `uv.lock`
- **Variables de entorno** personalizables

## 1.3. Estructura del Proyecto

```
.
├── .devcontainer/
│   ├── .env
│   ├── devcontainer.json
│   ├── docker-compose.yml
│   └── Dockerfile
├── config/
│   ├── database.env
│   ├── python.env
│   └── settings.env
├── docker/
│   └── Dockerfile
├── .envrc
├── LICENSE
└── README.md
```

### 1.4.2. Variables de entorno personalizables (`.env`)

> Se recomienda revisar los archivos de la carpeta `config/` para ajustes finales de la aplicación.

- `APP_NAME`: Nombre de la aplicación
- `USERNAME`: Usuario interno del devcontainer (`default: vscode`)

### 1.4.3. Iniciar Devcontainer

El devcontainer automáticamente:
- Instala Python y uv
- Sincroniza paquetes desde `uv.lock` (si existe)
- Configura el entorno de desarrollo
