# 📊 TaskPro - Sistema Profesional de Gestión de Tareas

Una aplicación web moderna y profesional para la gestión integral de tareas, proyectos y equipos. Implementa estructuras de datos lineales avanzadas como colas de prioridad (heap) para optimizar la gestión de tareas.

## ✨ Características Principales

### 1. **Gestión de Tareas Avanzada**
- Crear, editar y eliminar tareas
- Asignar tareas a miembros del equipo
- 4 niveles de prioridad: Crítica, Alta, Media, Baja
- 4 estados de tarea: Pendiente, En Progreso, Completada, Bloqueada
- Fechas de vencimiento y descripciones detalladas
- Búsqueda y filtrado en tiempo real

### 2. **Cola de Prioridad (MinHeap)**
- Implementación de estructura de datos Heap binario
- Ordenamiento automático de tareas por prioridad y fecha de vencimiento
- Vista dedicada "Cola de Prioridad" para ver tareas ordenadas por importancia
- Algoritmo optimizado O(log n) para inserciones y extracciones

### 3. **Gestión de Proyectos Profesional**
- Crear múltiples proyectos con descripción y fechas
- Asignar equipos a proyectos
- Visualizar estadísticas por proyecto
- Filtrar tareas por proyecto
- Cambiar entre proyectos fácilmente

### 4. **Gestión de Equipo**
- Agregar miembros del equipo con nombre y email
- Asignar tareas a miembros específicos
- Avatares con colores únicos para cada miembro
- Ver tareas asignadas a cada miembro
- Eliminar miembros del equipo

### 5. **Tablero Kanban Interactivo**
- 4 columnas: Pendientes, En Progreso, Completadas, Bloqueadas
- Drag & drop visual de tareas entre estados
- Cambiar estado directamente desde botones
- Color-coding por prioridad
- Contador de tareas por estado

### 6. **Dashboard Analítico**
- Total de tareas en el proyecto actual
- Distribución por prioridad
- Tareas asignadas por usuario
- Distribución por estado
- Próximas tareas ordenadas por prioridad
- Actualización en tiempo real

### 7. **Sistema de Reportes**
- Tasa de finalización de tareas
- Tareas completadas esta semana
- Tiempo promedio de finalización por tarea
- Contador de tareas vencidas
- Estadísticas detalladas por usuario
- Gráficos de progreso

### 8. **Filtros y Búsqueda Avanzada**
- Filtrar por proyecto
- Filtrar por usuario asignado
- Filtrar por prioridad
- Filtrar por estado
- Búsqueda en tiempo real por título y descripción
- Limpiar filtros con un clic

### 9. **Persistencia de Datos**
- Almacenamiento en LocalStorage
- Datos persisten entre sesiones
- Historial automático de cambios
- Opción para limpiar todos los datos

## 🛠️ Stack Tecnológico

- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **Backend**: Node.js + Express.js
- **Base de Datos**: LocalStorage
- **Iconos**: Font Awesome 6
- **Fuentes**: Google Fonts (Inter)

## 📦 Instalación y Uso

### Requisitos
- Node.js instalado
- npm (Node Package Manager)

### Pasos de Instalación

```bash
# 1. Navegar al directorio del proyecto
cd "Estructuras de datos lineales"

# 2. Instalar dependencias
npm install

# 3. Iniciar el servidor
npm start
```

El servidor se ejecutará en `http://localhost:3000`

## 📋 Estructura del Proyecto

```
Estructuras de datos lineales/
├── server.js           # Servidor Express
├── package.json        # Dependencias del proyecto
├── package-lock.json   # Versiones exactas de dependencias
└── public/
    └── index.html      # Aplicación web completa (HTML + CSS + JS)
```

## 🎯 Flujo de Trabajo

### Crear una Tarea
1. Ve a la pestaña **Tablero**
2. Haz clic en **+ Agregar Tarea** en la columna Pendientes
3. Completa el formulario:
   - Título (obligatorio)
   - Descripción
   - Proyecto
   - Prioridad (Crítica, Alta, Media, Baja)
   - Usuario asignado
   - Fecha de vencimiento
4. Guarda la tarea

### Asignar Tareas a Usuarios
1. Abre el formulario de nueva tarea
2. Selecciona un usuario en "Asignar a Usuario"
3. Guarda la tarea

### Cambiar Estado de Tarea
- En el tablero Kanban, usa el selector de estado en cada tarea
- O edita la tarea haciendo clic en "Editar"

### Ver Cola de Prioridad
1. En el tablero, haz clic en **Ver Cola de Prioridad**
2. Las tareas se mostrarán ordenadas automáticamente por:
   - Prioridad (Crítica → Alta → Media → Baja)
   - Fecha de vencimiento (más próxima primero)

### Crear Proyecto
1. Ve a **Proyectos**
2. Haz clic en **Nuevo Proyecto**
3. Completa:
   - Nombre
   - Descripción
   - Fechas (inicio y cierre estimada)
   - Equipo asignado
4. Guarda el proyecto

### Gestionar Equipo
1. Ve a **Equipo**
2. Agrega nuevos miembros con nombre y email
3. Visualiza todos los miembros y sus tareas asignadas
4. Elimina miembros si es necesario

## 📊 Colas de Prioridad - Implementación Técnica

### Clase MinHeap
La estructura de datos MinHeap implementada en el código permite:

```javascript
// Operaciones principales
heap.push(task)      // Insertar tarea - O(log n)
heap.pop()           // Extraer tarea prioritaria - O(log n)
heap.toArray()       // Obtener arreglo ordenado - O(n)
heap.isEmpty()       // Verificar si está vacío - O(1)
```

### Criterios de Ordenamiento
1. **Prioridad**: Crítica (0) → Alta (1) → Media (2) → Baja (3)
2. **Fecha de Vencimiento**: Las más próximas primero

### Visualización
La vista "Cola de Prioridad" muestra las tareas en orden de ejecución recomendado según su importancia.

## 🔐 Seguridad y Persistencia

- **LocalStorage**: Datos almacenados localmente en el navegador
- **Privacidad**: Ningún dato se envía a servidores externos
- **Backup**: Descarga tus datos antes de limpiar

## 🎨 Personalización

### Cambiar Usuario Actual
1. Ve a **Configuración**
2. Actualiza tu nombre en "Usuario Actual"
3. Tu avatar se actualizará automáticamente

### Colores de Miembros
Cada miembro del equipo obtiene un color único automáticamente. Los colores se asignan en orden: Azul, Rojo, Verde, Naranja, Púrpura, Cian.

## 💡 Conceptos de Estructuras de Datos Implementados

### 1. **Heap Binario (MinHeap)**
- Estructura de árbol completo
- Propiedad: Padre ≤ Hijos
- Operaciones: O(log n)
- Uso: Cola de prioridad para tareas

### 2. **Array Dinámico**
- Almacenamiento de tareas y proyectos
- Filtrado y búsqueda: O(n)
- Acceso directo: O(1)

### 3. **Diccionarios/Objetos**
- Mapeo de proyectos y usuarios por ID
- Acceso O(1) a elementos

### 4. **Algoritmos**
- Comparación personalizada de elementos
- Bubble Up/Down en heap
- Filtrado con predicados
- Búsqueda por patrón

## 📈 Estadísticas Disponibles

### Dashboard
- Total de tareas
- Distribución por prioridad
- Tareas por usuario
- Distribución por estado

### Reportes
- Tasa de finalización (%)
- Tareas completadas
- Tiempo promedio por tarea
- Tareas vencidas
- Progreso por usuario

## 🚀 Mejoras Futuras

- [ ] Exportar reportes a PDF
- [ ] Colaboración en tiempo real
- [ ] Notificaciones de vencimiento
- [ ] Integración con calendario
- [ ] Etiquetas y categorías personalizadas
- [ ] Historial de cambios
- [ ] Integración con APIs externas
- [ ] Modo oscuro

## 📝 Notas de Desarrollo

- El proyecto utiliza **Vanilla JavaScript** sin dependencias externas en el frontend
- **Express.js** sirve solo para hospedar archivos estáticos
- Los datos se sincronizan automáticamente con LocalStorage
- La interfaz es **responsive** y funciona en dispositivos móviles

## 🤝 Contribuciones

Este proyecto es educativo y demostrativo de conceptos de estructuras de datos. Siéntete libre de modificarlo y mejorarlo según tus necesidades.

## 📄 Licencia

Proyecto de demostración educativa - Libre para usar y modificar.

---

**Creado con ❤️ para la gestión profesional de tareas**
