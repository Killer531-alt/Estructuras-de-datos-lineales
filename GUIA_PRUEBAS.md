# ✅ Guía de Prueba - TaskPro v2.1

## Verificación Rápida de Funcionalidades

### Test 1: Crear Tarea y Verificar Sincronización

**Pasos**:
1. Abre http://localhost:3000
2. Ve a **Tablero** 
3. Haz clic en **+ Agregar Tarea**
4. Completa el formulario:
   - Título: "Test de sincronización"
   - Prioridad: "Alta"
   - Asignar a: "Jane Smith"
5. Haz clic en **Guardar Tarea**

**Verifica que**:
- [ ] La tarea aparece en la columna "Pendientes" del tablero
- [ ] El contador "📋 Pendientes" se incrementa
- [ ] El Dashboard muestra la nueva tarea en "Total de Tareas"
- [ ] Dashboard muestra a Jane Smith con una tarea asignada
- [ ] Dashboard incrementa "Tareas por Prioridad" en "Alta"

---

### Test 2: Asignar Tarea a Usuario

**Pasos**:
1. En el Tablero, haz clic en **Editar** en una tarea
2. Cambia "Asignar a Usuario" a "Bob Wilson"
3. Haz clic en **Guardar Cambios**

**Verifica que**:
- [ ] La tarea ahora muestra el avatar y nombre de Bob Wilson
- [ ] Dashboard actualiza "Tareas por Usuario"
- [ ] Reportes reflejan el nuevo cambio
- [ ] Los números de asignaciones se ajustan

---

### Test 3: Cambiar Estado de Tarea

**Pasos**:
1. En el Tablero, en cualquier tarea, haz clic en el selector de estado
2. Cambia a "En Progreso"

**Verifica que**:
- [ ] La tarea se mueve a la columna "En Progreso"
- [ ] El contador de "Pendientes" disminuye
- [ ] El contador de "En Progreso" aumenta
- [ ] Dashboard actualiza las estadísticas
- [ ] Reportes muestran "Tareas completadas" actualizado

---

### Test 4: Ver Cola de Prioridad

**Pasos**:
1. En el Tablero, haz clic en **Ver Cola de Prioridad**
2. Observa el orden de las tareas

**Verifica que**:
- [ ] Las tareas críticas están primero
- [ ] Luego las altas, medias y bajas
- [ ] Dentro de cada nivel, las fechas más próximas están primero
- [ ] Cada tarea muestra su usuario asignado

---

### Test 5: Agregar Miembro del Equipo

**Pasos**:
1. Ve a **Equipo**
2. Ingresa:
   - Nombre: "Carlos López"
   - Email: "carlos@example.com"
3. Haz clic en **Agregar**

**Verifica que**:
- [ ] El nuevo miembro aparece en la lista de equipo
- [ ] Tiene un avatar con color único
- [ ] Está disponible en el selector de asignación (modal de tarea)
- [ ] Dashboard actualiza con el nuevo miembro en "Tareas por Usuario"
- [ ] Puedes asignar tareas al nuevo miembro

---

### Test 6: Crear Proyecto

**Pasos**:
1. Ve a **Proyectos**
2. Haz clic en **Nuevo Proyecto**
3. Completa:
   - Nombre: "Proyecto de Prueba"
   - Descripción: "Testing del sistema"
   - Equipo: Selecciona algunos miembros
4. Haz clic en **Crear Proyecto**

**Verifica que**:
- [ ] El proyecto aparece en la lista
- [ ] El proyecto está disponible en el selector de proyectos
- [ ] Puedes abrir el proyecto
- [ ] Las tareas se filtran por proyecto

---

### Test 7: Filtrado de Tareas

**Pasos**:
1. Ve a **Tablero**
2. Establece filtros:
   - Usuario: "Jane Smith"
   - Prioridad: "Alta"
3. Observa los resultados

**Verifica que**:
- [ ] Solo aparecen tareas asignadas a Jane
- [ ] Solo aparecen tareas de prioridad alta
- [ ] Los contadores se ajustan
- [ ] El botón "Limpiar Filtros" funciona

---

### Test 8: Dashboard en Tiempo Real

**Pasos**:
1. Abre Dashboard en una pestaña
2. En otra pestaña abre Tablero
3. Crea/edita una tarea en el Tablero
4. Vuelve a Dashboard

**Verifica que**:
- [ ] Dashboard muestra los cambios
- [ ] No es necesario recargar la página
- [ ] Las estadísticas son precisas

---

### Test 9: Reportes

**Pasos**:
1. Ve a **Reportes**
2. Completa algunas tareas en el Tablero
3. Vuelve a Reportes

**Verifica que**:
- [ ] "Tareas Completadas" aumenta
- [ ] "Tasa de Finalización" se actualiza
- [ ] "Tareas por Usuario" muestra datos correctos
- [ ] "Tareas Vencidas" se calcula correctamente

---

### Test 10: Sincronización Global

**Pasos**:
1. Abre 3 tabs del navegador con TaskPro
2. En tab 1, crea una tarea
3. En tab 2, crea un proyecto
4. En tab 3, agrega un miembro

**Verifica que**:
- [ ] Los datos se guardan correctamente
- [ ] Recargando una página, los datos persisten
- [ ] Los datos son consistentes entre operaciones

---

## Checklist de Funcionalidades Críticas

### Tareas
- [ ] Crear tarea
- [ ] Editar tarea
- [ ] Eliminar tarea
- [ ] Cambiar estado de tarea
- [ ] Asignar tarea a usuario
- [ ] Ver tarea en múltiples lugares (tablero, dashboard, cola de prioridad)

### Usuarios/Equipo
- [ ] Agregar miembro del equipo
- [ ] Eliminar miembro del equipo
- [ ] Ver lista de miembros
- [ ] Ver tareas asignadas a cada miembro
- [ ] Los cambios se reflejan en asignaciones de tareas

### Proyectos
- [ ] Crear proyecto
- [ ] Editar proyecto
- [ ] Eliminar proyecto
- [ ] Ver lista de proyectos
- [ ] Cambiar entre proyectos
- [ ] Filtrar tareas por proyecto

### Vistas
- [ ] **Dashboard**: Muestra estadísticas en tiempo real
- [ ] **Tablero**: Muestra tareas por estado
- [ ] **Cola de Prioridad**: Ordena tareas correctamente
- [ ] **Reportes**: Calcula estadísticas con precisión
- [ ] **Equipo**: Gestiona miembros del equipo
- [ ] **Proyectos**: Gestiona proyectos
- [ ] **Configuración**: Permite cambiar usuario actual

### Filtros y Búsqueda
- [ ] Filtrar por usuario
- [ ] Filtrar por prioridad
- [ ] Filtrar por estado
- [ ] Buscar por título o descripción
- [ ] Limpiar filtros

---

## Pruebas de Rendimiento

### Test de Carga

**Pasos**:
1. Abre Herramientas de Desarrollador (F12)
2. Ve a **Rendimiento/Performance**
3. Crea 10 tareas rápidamente
4. Observa el rendimiento

**Esperado**:
- [ ] La aplicación responde rápidamente
- [ ] No hay lag perceptible
- [ ] El uso de memoria es razonable

---

## Pruebas de Persistencia

**Pasos**:
1. Crea varios proyectos y tareas
2. Cierra completamente el navegador
3. Reabre y vuelve a TaskPro

**Verifica que**:
- [ ] Todos los datos persisten
- [ ] La estructura está intacta
- [ ] No hay pérdida de datos

---

## Solución de Problemas Comunes

### Problema: Datos no aparecen después de crear

**Solución**:
1. Verifica que el proyecto actual sea correcto
2. Revisa los filtros (puede haber un filtro activo)
3. Recarga la página (Ctrl+R o F5)
4. Abre la consola (F12) y busca errores

### Problema: Usuario no aparece en asignación

**Solución**:
1. Ve a Equipo y verifica que esté agregado
2. Recarga la página
3. Intenta crear un nuevo usuario

### Problema: Tarea aparece en un lado pero no en otro

**Solución**:
1. Abre la consola (F12) y revisa errores
2. Recarga la página (Ctrl+R)
3. Limpia localStorage: Abre Configuración → Limpiar Todos los Datos
4. Recrea los datos

---

## Notas Importantes

⚠️ **LocalStorage tiene límite**: ~5-10MB
- Si tienes muchas tareas (>10,000), considera usar IndexedDB

⚠️ **Rendimiento puede degradarse** con:
- >1,000 tareas por proyecto
- >100 miembros del equipo

✅ **Recomendaciones**:
- Limpia proyectos completados regularmente
- Archiva tareas antiguas
- Limpia datos sin usar

---

**¡Listo! Si todos los tests pasan, TaskPro v2.1 está funcionando correctamente.** ✅
