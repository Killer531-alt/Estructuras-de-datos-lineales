# 🔧 Documentación Técnica - TaskPro

## Estructura de Datos y Algoritmos

### 1. MinHeap (Heap Binario Mínimo)

#### Definición
Un **Heap Binario** es un árbol binario completo que cumple con la propiedad de heap:
- **Min-Heap**: Cada padre es menor o igual que sus hijos
- **Usado en**: Cola de Prioridad

#### Implementación en TaskPro

```javascript
class MinHeap {
  constructor() {
    this.heap = [];  // Array para almacenar elementos
  }

  // Operación: Insertar elemento
  push(task) {
    this.heap.push(task);
    this.bubbleUp(this.heap.length - 1);
  }
  // Complejidad: O(log n)

  // Operación: Extraer mínimo
  pop() {
    if (this.heap.length === 0) return null;
    if (this.heap.length === 1) return this.heap.pop();
    const min = this.heap[0];
    this.heap[0] = this.heap.pop();
    this.bubbleDown(0);
    return min;
  }
  // Complejidad: O(log n)
}
```

#### Visualización de un Heap

```
        [Critical, 2024-11-23]              (Nivel 0)
       /                    \
   [High, 2024-11-24]   [High, 2024-11-25]  (Nivel 1)
   /        \            /         \
[Med]    [Med]       [Low]      [Low]        (Nivel 2)

Almacenado como array:
[Critical, High, High, Med, Med, Low, Low]
       0      1     2    3    4   5    6
```

#### Operaciones Principales

**BubbleUp** (Después de insertar):
```
Nuevo elemento: [High, 2024-11-24]
Posición inicial: índice 6
Compara con padre (índice 2)
Si es menor, intercambia y sube nuevamente
O(log n) en peor caso
```

**BubbleDown** (Después de remover raíz):
```
Elemento removido del final va al inicio
Mueve elemento grande hacia abajo
Intercambia con hijo más pequeño
O(log n) en peor caso
```

#### Comparación de Tareas

```javascript
compareTasks(a, b) {
  // 1. Comparar por prioridad (crítica < alta < media < baja)
  const priorityOrder = { critical: 0, high: 1, medium: 2, low: 3 };
  const aPriority = priorityOrder[a.priority];
  const bPriority = priorityOrder[b.priority];

  if (aPriority !== bPriority) {
    return aPriority - bPriority;  // Menor valor = mayor prioridad
  }

  // 2. Si mismo nivel, comparar por fecha de vencimiento
  if (a.dueDate && b.dueDate) {
    return new Date(a.dueDate) - new Date(b.dueDate);
    // Fecha más próxima = mayor prioridad
  }

  return 0;
}
```

#### Ejemplo de Uso en TaskPro

```javascript
// Crear heap
const heap = new MinHeap();

// Agregar tareas
heap.push({ id: '1', title: 'Bug', priority: 'critical', dueDate: '2024-11-23' });
heap.push({ id: '2', title: 'Feature', priority: 'high', dueDate: '2024-11-25' });
heap.push({ id: '3', title: 'Doc', priority: 'low', dueDate: '2024-12-01' });

// Obtener tareas ordenadas
const ordered = heap.toArray();
// Resultado: [Bug (crítica), Feature (alta), Doc (baja)]

// Extraer tarea más prioritaria
const nextTask = heap.pop();
// nextTask = { id: '1', title: 'Bug', ... }
```

### 2. Estructura de Datos - Tareas

#### Modelo de Tarea

```javascript
{
  id: "1700732400000",              // ID único (timestamp)
  title: "Corregir bug de login",   // Título obligatorio
  description: "El login no...",     // Descripción detallada
  projectId: "default",              // Proyecto asociado
  priority: "critical",              // critical|high|medium|low
  status: "pending",                 // pending|in-progress|completed|blocked
  assignee: "1",                     // ID del usuario asignado
  dueDate: "2024-12-01",             // Fecha de vencimiento (YYYY-MM-DD)
  createdAt: "2024-11-23T10:00:00Z", // Timestamp ISO
  completedAt: null                  // Timestamp ISO cuando se completó
}
```

#### Almacenamiento

```javascript
// Array de tareas
let tasks = [
  { id: '1', title: 'Bug crítico', projectId: 'default', ... },
  { id: '2', title: 'Feature A', projectId: 'project1', ... },
  { id: '3', title: 'Documento', projectId: 'project1', ... }
];

// Persistencia: localStorage
localStorage.setItem('tasks', JSON.stringify(tasks));
let loadedTasks = JSON.parse(localStorage.getItem('tasks'));
```

### 3. Estructura de Datos - Proyectos

```javascript
{
  id: "1700732400001",
  name: "Desarrollo Web",
  description: "Crear sitio web para cliente",
  startDate: "2024-11-23",
  endDate: "2024-12-23",
  team: ["1", "2", "3"],             // IDs de miembros del equipo
  tasks: []                          // (Deprecated) Se usa array tasks
}
```

### 4. Estructura de Datos - Miembros del Equipo

```javascript
{
  id: "1",
  name: "Jane Smith",
  email: "jane@example.com",
  initials: "JS",                    // Calculado: primeras letras
  color: "#e74c3c"                   // Color único para avatar
}
```

### 5. Algoritmos de Búsqueda y Filtrado

#### Búsqueda de Tareas

```javascript
function performSearch() {
  const query = document.getElementById('search-input').value.toLowerCase();
  
  // O(n) - Busca lineal en todas las tareas
  const filtered = projectTasks.filter(task =>
    task.title.toLowerCase().includes(query) ||
    task.description.toLowerCase().includes(query)
  );

  renderBoard(filtered);
}
```

**Complejidad**: O(n) donde n = número de tareas

#### Filtrado Avanzado

```javascript
function applyFiltersToTasks(taskList) {
  // O(n) - Filtrado con múltiples predicados
  return taskList.filter(task => {
    // Todos deben cumplirse (AND)
    if (filters.user && task.assignee !== filters.user) return false;
    if (filters.priority && task.priority !== filters.priority) return false;
    if (filters.status && task.status !== filters.status) return false;
    return true;
  });
}
```

**Complejidad**: O(n) con k filtros = O(n*k)

#### Búsqueda de Elemento Específico

```javascript
// Buscar tarea por ID
const task = tasks.find(t => t.id === taskId);
// Complejidad: O(n)

// Mejor con índice (si hubiera muchas tareas):
// const taskMap = {}
// tasks.forEach(t => taskMap[t.id] = t);
// const task = taskMap[taskId];  // O(1)
```

## Complejidad de Operaciones

| Operación | Complejidad | Notas |
|-----------|------------|-------|
| Crear tarea | O(1) | Push a array |
| Editar tarea | O(n) | Búsqueda + actualización |
| Eliminar tarea | O(n) | Búsqueda + splice |
| Buscar por ID | O(n) | Búsqueda lineal |
| Filtrar tareas | O(n*k) | n=tareas, k=filtros |
| Ordenar por prioridad | O(n log n) | Sort con comparador |
| Cola de prioridad push | O(log n) | Heap insert |
| Cola de prioridad pop | O(log n) | Heap extract |
| Contar tareas por estado | O(n) | Recuento lineal |

## Optimizaciones Realizadas

### 1. Carga Inicial
```javascript
// Se cargan todos los datos una sola vez
let tasks = JSON.parse(localStorage.getItem('tasks')) || [];
let projects = JSON.parse(localStorage.getItem('projects')) || {};

// En lugar de leerlos múltiples veces
```

### 2. Filtrado en Cliente
```javascript
// Todos los filtros se aplican en el navegador (O(n))
// Mejor que hacer múltiples queries a servidor
const filtered = applyFiltersToTasks(projectTasks);
```

### 3. Renderizado Selectivo
```javascript
// Solo se renderiza lo visible
renderTaskList(filtered.filter(t => t.status === 'pending'), 'pending-list');

// En lugar de renderizar todo y ocultarlo
```

### 4. Uso de Heap para Cola de Prioridad
```javascript
// Inserción O(log n) en lugar de:
// - Sort completo: O(n log n)
// - Búsqueda lineal: O(n)
const heap = new MinHeap();
heap.push(task);  // O(log n)
```

## Flujo de Datos

### Crear Tarea
```
1. Usuario llena formulario en modal
2. JavaScript captura valores
3. Crea objeto Task nuevo
4. Inserta en array tasks
5. Guarda en localStorage
6. Renderiza tablero
7. Actualiza estadísticas
```

### Cambiar Estado de Tarea
```
1. Usuario selecciona nuevo estado
2. Se busca la tarea por ID (O(n))
3. Se actualiza propiedad status
4. Se guarda en localStorage
5. Se renderiza tablero
6. Se actualiza heap si es necesario
```

### Aplicar Filtros
```
1. Usuario cambia selector de filtro
2. Se llama applyFilters()
3. Se crean predicados según filtros
4. Se filtra array tasks (O(n*k))
5. Se renderiza solo tareas filtradas
6. Se actualizan contadores
```

## Mejoras Futuras (Rendimiento)

### Corto Plazo
- [ ] Indexación de tareas por ID (Object en lugar de Array)
- [ ] Caché de búsquedas frecuentes
- [ ] Virtualización de listas grandes (>1000 tareas)

### Mediano Plazo
- [ ] IndexedDB en lugar de localStorage (más capacidad)
- [ ] Service Workers para trabajar offline
- [ ] Sincronización con servidor

### Largo Plazo
- [ ] Base de datos real (PostgreSQL)
- [ ] GraphQL para queries optimizadas
- [ ] WebSockets para colaboración en tiempo real

## Testing de Estructuras de Datos

### Probar Heap
```javascript
// Test: Insertar y extraer en orden
const heap = new MinHeap();
heap.push({ priority: 'low', dueDate: '2024-12-10' });
heap.push({ priority: 'critical', dueDate: '2024-11-25' });
heap.push({ priority: 'high', dueDate: '2024-11-24' });

const first = heap.pop();  // Debe ser crítica 2024-11-25
const second = heap.pop();  // Debe ser alta 2024-11-24
const third = heap.pop();   // Debe ser baja 2024-12-10
```

### Probar Filtrado
```javascript
// Test: Filtros múltiples
const tasks = [
  { id: '1', priority: 'high', assignee: 'user1', status: 'pending' },
  { id: '2', priority: 'high', assignee: 'user2', status: 'pending' },
  { id: '3', priority: 'low', assignee: 'user1', status: 'pending' }
];

filters = { priority: 'high', assignee: 'user1' };
const result = applyFiltersToTasks(tasks);
// Debe retornar solo tarea 1
```

## Ecuaciones de Complejidad

### Crear Múltiples Tareas
```
Crear n tareas = O(1) * n = O(n)
Renderizar = O(n log n) (sort)
Total = O(n log n)
```

### Buscar y Filtrar
```
Buscar: O(n)
Filtrar con k criterios: O(n * k)
Si k es pequeño (≤5): O(n)
```

### Cola de Prioridad con n Tareas
```
Operación push: O(log n)
Operación pop: O(log n)
Obtener array ordenado: O(n)
```

## Patrones de Diseño Utilizados

### 1. Singleton Pattern
```javascript
// Una única instancia de la aplicación
const app = {
  currentUser,
  teamMembers,
  projects,
  tasks
};
```

### 2. Observer Pattern
```javascript
// Event listeners en elementos del DOM
document.getElementById('filter-priority').addEventListener('change', applyFilters);
```

### 3. Factory Pattern
```javascript
// Crear objetos de tarea
const task = {
  id: Date.now().toString(),
  title,
  // ... más propiedades
};
```

---

**Documentación técnica completa para desarrolladores** 📚
