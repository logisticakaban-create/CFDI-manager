# Sistema de Gestión CFDI - Exportación Completa

## Descripción del Sistema

Este es un sistema completo para gestión de CFDIs (Comprobantes Fiscales Digitales) con conexión real a Odoo.

## Arquitectura del Proyecto

### Backend (Node.js + Express + TypeScript)
- **server/services/odoo.ts**: Servicio principal de conexión a Odoo con APIs reales
- **server/routes.ts**: Rutas de API para manejo de CFDIs, descargas, y emails
- **server/storage.ts**: Capa de almacenamiento con interfaz abstracta
- **server/index.ts**: Servidor principal Express

### Frontend (React + TypeScript + Tailwind)
- **client/src/components/**: Componentes de UI incluyendo tablas, filtros, setup de conexión
- **client/src/pages/**: Páginas principales (dashboard, not-found)
- **client/src/lib/**: Utilidades y configuración de React Query

### Esquemas Compartidos
- **shared/schema.ts**: Esquemas de datos con Drizzle ORM y validaciones Zod

## Características Principales

### ✅ Funcionalidades Implementadas
1. **Conexión Real a Odoo**: Autenticación y conexión directa a bases de datos Odoo
2. **Descarga de CFDIs Auténticos**: Solo archivos reales desde Odoo (XML/PDF)
3. **Filtrado Avanzado**: Por fecha, partner, UUID, RFC emisor, tipo de documento
4. **Descarga Individual y Masiva**: ZIP con archivos reales
5. **Sistema de Email**: Integración con mailto: del sistema operativo
6. **Multi-empresa**: Soporte para múltiples empresas en una instancia Odoo
7. **Interfaz Responsive**: UI moderna con Tailwind CSS y componentes Shadcn/UI

### 🔧 Tecnologías Utilizadas
- **Backend**: Express.js, TypeScript, XML-RPC para Odoo
- **Frontend**: React 18, TypeScript, React Query, Wouter (routing)
- **UI**: Tailwind CSS, Shadcn/UI components, Radix UI primitives
- **Base de Datos**: Soporte para PostgreSQL con Drizzle ORM
- **Validación**: Zod schemas para type safety
- **Email**: Nodemailer + integración nativa del SO

## Instalación y Configuración

### Dependencias
```bash
npm install
```

### Variables de Entorno Requeridas
```env
# PostgreSQL (opcional)
DATABASE_URL=postgresql://...

# Email SMTP (opcional)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=tu-email@gmail.com
SMTP_PASS=tu-password
```

### Ejecutar el Sistema
```bash
npm run dev
```

El servidor se ejecuta en puerto 5000 con frontend y backend integrados.

## Configuración de Conexión Odoo

### Datos Requeridos
1. **URL de Odoo**: https://tu-instancia.odoo.com
2. **Base de Datos**: nombre_de_tu_bd
3. **Usuario**: tu-usuario
4. **Contraseña**: tu-contraseña

### Proceso de Conexión
1. El sistema autentica via XML-RPC
2. Obtiene lista de empresas disponibles
3. Carga CFDIs reales desde account.move
4. Permite descarga de attachments XML/PDF existentes

## Estructura de Archivos Críticos

```
server/
├── services/odoo.ts     # 🔥 CRÍTICO: Conexión real a Odoo
├── routes.ts           # 🔥 CRÍTICO: APIs de descarga y manejo
└── storage.ts          # Capa de datos abstracta

client/src/
├── components/
│   ├── documents-table.tsx  # Tabla principal de CFDIs
│   ├── filters-panel.tsx    # Panel de filtros avanzados
│   └── connection-setup.tsx # Setup de conexión Odoo
└── pages/dashboard.tsx      # Dashboard principal

shared/schema.ts        # 🔥 CRÍTICO: Esquemas de datos
```

## Notas Importantes

### ❌ Problemas Conocidos
1. **Campo Odoo**: El campo `l10n_mx_edi_cfdi` no existe en todas las versiones
2. **Attachments**: Los PDFs deben existir como attachments en Odoo
3. **Limitación Email**: mailto: no puede adjuntar archivos automáticamente

### ✅ Soluciones Implementadas
1. **Solo Datos Reales**: No genera contenido falso
2. **Manejo de Errores**: Errores claros cuando no hay archivos
3. **Filtrado Funcional**: Filtros que funcionan con datos reales de Odoo
4. **Estabilidad**: Sistema robusto sin crashes

## Estado del Proyecto

**Última Actualización**: 30 Enero 2025

El sistema está configurado para trabajar ÚNICAMENTE con datos reales de Odoo. No genera contenido falso ni maquetas. Todos los archivos descargados provienen directamente de la base de datos Odoo.

Para usar este código con otra IA:
1. Importa todos los archivos
2. Instala dependencias: `npm install`
3. Configura variables de entorno
4. Ejecuta: `npm run dev`
5. Configura conexión Odoo en la interfaz

El código está listo para producción con datos reales de Odoo.