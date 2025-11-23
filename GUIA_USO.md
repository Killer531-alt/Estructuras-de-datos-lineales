# 🎓 Guía de Uso - TaskPro

## Primeros Pasos

### 1. Inicializar la Aplicación

Cuando abres TaskPro por primera vez, verás:
- **Usuario predeterminado**: John Doe
- **3 miembros de equipo**: John Doe, Jane Smith, Bob Wilson
- **1 proyecto**: Proyecto Principal
- **0 tareas**: Sin tareas iniciales

### 2. Configurar tu Equipo

#### Paso A: Cambiar el Usuario Actual
1. Abre **Configuración** (⚙️ en el sidebar)
2. Encuentra "Usuario Actual"
3. Ingresa tu nombre en el campo de texto
4. Haz clic en **Actualizar**

Tu avatar se actualizará automáticamente en la esquina superior derecha.

#### Paso B: Agregar o Modificar Miembros del Equipo
1. Ve a **Equipo** (👥 en el sidebar)
2. En "Agregar Miembro del Equipo", ingresa:
   - **Nombre**: Nombre completo del miembro
   - **Email**: Correo electrónico
3. Haz clic en **Agregar**

El nuevo miembro aparecerá en la lista con un avatar y color único.

### 3. Crear un Proyecto

1. Ve a **Proyectos** (📁 en el sidebar)
2. Haz clic en **Nuevo Proyecto**
3. Completa el formulario:
   ```
   Nombre del Proyecto: "Desarrollo Web"
   Descripción: "Crear sitio web para cliente"
   Fecha de Inicio: 2024-11-23
   Fecha de Cierre Estimada: 2024-12-23
   Equipo: Selecciona los miembros a asignar
   ```
4. Haz clic en **Crear Proyecto**

El nuevo proyecto aparecerá en la lista. Puedes cambiar de proyecto haciendo clic en **Abrir**.

### 4. Crear Tareas

#### Opción A: Desde el Tablero
1. Ve a **Tablero** (📋 en el sidebar)
2. En la columna "📋 Pendientes", haz clic en **+ Agregar Tarea**
3. Completa el formulario:
   ```
   Título: "Diseñar interfaz principal"
   Descripción: "Crear mockups de la página de inicio"
   Proyecto: "Desarrollo Web"
   Prioridad: "Alta"
   Asignar a Usuario: "Jane Smith"
   Fecha de Vencimiento: 2024-12-01
   ```
4. Haz clic en **Guardar Tarea**

La tarea aparecerá en la columna "Pendientes".

## 📊 Flujo de Trabajo Recomendado

### Ejemplo: Gestionar un Sprint

**Lunes - Planificación**
1. Crea 5-7 tareas principales para la semana
2. Asigna prioridades: 1-2 Críticas, 2-3 Altas, 2-3 Medias
3. Asigna cada tarea a un miembro específico
4. Revisa la "Cola de Prioridad" para orden de ejecución

**Martes a Jueves - Ejecución**
1. Ve a **Tablero**
2. Abre las tareas de mayor prioridad
3. Cambia el estado a "En Progreso" cuando empieces
4. Actualiza la descripción con avances
5. Cambia a "Completada" al terminar

**Viernes - Reportes**
1. Ve a **Reportes**
2. Analiza:
   - Tareas completadas esta semana
   - Tasa de finalización
   - Tiempo promedio por tarea
   - Desempeño de cada miembro

## 🎯 Casos de Uso

### Caso 1: Gestión de Bugs

**Crear tarea de bug crítico:**
```
Título: "Login no funciona en mobile"
Prioridad: "Crítica"
Asignar a: "Bob Wilson" (experto en mobile)
Fecha de Vencimiento: Hoy
Estado: "Pendiente"
```

**Seguimiento:**
- Bob cambia a "En Progreso" cuando comienza
- Actualiza la descripción con investigaciones
- Cambia a "Completada" cuando se resuelve

### Caso 2: Gestión de Proyecto Grande

**Crear proyecto:**
```
Nombre: "Migración a Base de Datos"
Descripción: "Migrar datos legacy a PostgreSQL"
Equipo: John, Jane, Bob
```

**Crear tareas relacionadas:**
- "Análisis de datos existentes" - Media - John
- "Diseño del nuevo esquema" - Alta - Jane
- "Desarrollo de scripts de migración" - Crítica - Bob
- "Testing de integridad de datos" - Alta - John
- "Documentación del proceso" - Baja - Jane

**Ver progreso:**
1. Ve a **Dashboard** para ver resumen general
2. Ve a **Tablero** para detalles específicos
3. Ve a **Reportes** para estadísticas

## 🔍 Búsqueda y Filtrado

### Búsqueda por Título o Descripción
1. Ve a **Tablero**
2. En la barra de búsqueda superior, escribe:
   - "login" para encontrar tareas sobre login
   - "migration" para encontrar tareas de migración

### Filtrado Avanzado

En el **Tablero**, usa los filtros:

**Filtro 1: Por Usuario**
```
Usuario Asignado: "Jane Smith"
```
Verás solo tareas asignadas a Jane.

**Filtro 2: Por Prioridad**
```
Prioridad: "Crítica"
```
Verás solo tareas críticas.

**Filtro 3: Por Estado**
```
Estado: "En Progreso"
```
Verás solo tareas en progreso.

**Filtro 4: Combinado**
```
Usuario: "Bob Wilson"
Prioridad: "Alta"
Estado: "Pendiente"
```
Verás tareas altas pendientes asignadas a Bob.

**Limpiar filtros:**
Haz clic en el botón **Limpiar Filtros** para resetear todo.

## ⭐ Cola de Prioridad

Esta es una característica única que implementa un **Heap Binario**.

### Cómo Funciona

El sistema ordena automáticamente las tareas por:
1. **Nivel de Prioridad** (Crítica → Alta → Media → Baja)
2. **Fecha de Vencimiento** (más próxima primero)

### Cómo Usarla

1. Ve a **Tablero**
2. Haz clic en el botón **Ver Cola de Prioridad**
3. Verás todas tus tareas ordenadas por importancia

**Ejemplo de orden:**
```
Prioridad #1: Bug crítico de login (Crítica, vence hoy)
Prioridad #2: Feature A (Crítica, vence mañana)
Prioridad #3: Feature B (Alta, vence en 2 días)
Prioridad #4: Documentación (Baja, sin fecha)
```

### Beneficio

Sabes exactamente qué tarea hacer primero según urgencia e importancia.

## 📈 Analizar Reportes

### Dashboard
Información general del proyecto actual:
- **Total de Tareas**: Cuántas tareas hay en total
- **Tareas por Prioridad**: Distribución visual
- **Tareas por Usuario**: Carga de trabajo
- **Tareas por Estado**: Progreso general
- **Próximas Tareas**: Top 5 ordenadas por prioridad

### Reportes Detallados
Ve a **Reportes** para ver:

| Métrica | Significado | Ejemplo |
|---------|------------|---------|
| Tareas Completadas | Cuántas finalizaste | 12 esta semana |
| Tasa de Finalización | Porcentaje completado | 60% del total |
| Tiempo Promedio | Cuánto tarda terminar una | 24h por tarea |
| Tareas Vencidas | Cuántas pasaron fecha | 3 requieren atención |
| Tareas por Usuario | Productividad individual | Jane: 5, Bob: 3 |

## 💾 Guardar y Restaurar Datos

### Datos se Guardan Automáticamente
- Cada vez que creas/editas/eliminas algo
- Se guarda en LocalStorage del navegador
- Los datos persisten al cerrar la pestaña

### Limpiar Todos los Datos

⚠️ **ADVERTENCIA**: Esta acción no se puede deshacer

1. Ve a **Configuración**
2. En "Datos", haz clic en **Limpiar Todos los Datos**
3. Confirma la acción
4. Se eliminará TODO: proyectos, tareas, equipo

## 🎨 Consejos de Uso Profesional

### 1. Usar Prioridades Correctamente

**Crítica**: Bloquea otros trabajos o tiene consecuencias graves
- Bugs en producción
- Tareas bloqueantes
- Deadlines muy cercanos

**Alta**: Importante pero no bloquea todo
- Features para el siguiente release
- Tareas de impacto medio
- Deadlines en 1-2 semanas

**Media**: Necesarias pero flexible
- Mejoras menores
- Optimizaciones
- Documentación

**Baja**: Nice-to-have
- Refactoring
- Mejoras UX menores
- Tech debt

### 2. Asignar Tareas Efectivamente

- Asigna a quien tiene **expertise** en el tema
- Considera la **carga actual** del miembro
- Revisa tareas en progreso antes de agregar nuevas
- Comunica claramente en la descripción

### 3. Usar Fechas de Vencimiento

- **Críticas**: Fecha de hoy o mañana
- **Altas**: 3-7 días
- **Medias**: 1-2 semanas
- **Bajas**: Opcional o abierta

### 4. Revisar Regularmente

- **Diario**: Revisa tareas "En Progreso"
- **Semanal**: Revisa Reportes y actualiza estado
- **Mensual**: Analiza tendencias de productividad

## 🐛 Solución de Problemas

### Problema: Datos desaparecieron
**Solución**: Revisa que estés en el mismo navegador y proyecto

### Problema: No veo tareas creadas
**Solución**: 
1. Verifica que estés en el proyecto correcto
2. Revisa los filtros (puede haber un filtro activo)
3. Limpia filtros con el botón "Limpiar Filtros"

### Problema: Miembro del equipo no aparece en asignación
**Solución**:
1. Ve a **Equipo** y verifica que esté agregado
2. Recarga la página (F5)
3. Si persiste, elimina y vuelve a agregar

### Problema: La cola de prioridad se ve extraña
**Solución**: Es normal que se reordene. Está funcionando correctamente si:
- Las críticas están primero
- Después las altas, luego medias y bajas
- Dentro de cada prioridad, más próximas al inicio

---

**¡Listo! Ya estás preparado para usar TaskPro profesionalmente. 🚀**
