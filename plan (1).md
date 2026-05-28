# 📊 Plan: Dashboard Estadístico de Encuesta
> Stack: HTML + CSS + JavaScript + Tailwind CSS + Chart.js / ApexCharts

---

## 🎯 Objetivo

Construir un dashboard web **single-file** (un solo `.html`) que cargue el archivo JSON de respuestas y presente los datos de forma visual, interactiva y profesional — listo para presentar ante una audiencia.

---

## 🗂️ Estructura del Proyecto

```
dashboard/
├── index.html          ← Archivo único con todo integrado
├── data.json           ← Tu archivo de respuestas (se carga localmente)
└── plan.md             ← Este archivo
```

> **Nota:** Todo el CSS, JS y HTML vive en `index.html`. El JSON se carga con `fetch('./data.json')` o se puede pegar directamente como variable JS si prefieres distribuir sin servidor.

---

## 🧱 Fases de Desarrollo

### Fase 1 — Análisis del JSON (30 min)
**Antes de escribir código**, mapear la estructura real del archivo:

- [ ] Identificar las **claves** de cada respuesta (ej: `edad`, `genero`, `pregunta_1`, etc.)
- [ ] Clasificar cada campo:
  - **Demográfico** → edad, género, ciudad, escolaridad, etc.
  - **Escala** → valores numéricos (1–5 o 1–10)
  - **Opción múltiple** → valores de texto / categorías
  - **Sí/No** → booleanos o strings "Sí"/"No"
- [ ] Detectar campos vacíos o inconsistencias en los datos
- [ ] Decidir qué variables son **ejes de filtro** (ej: filtrar por género o rango de edad)

**Entregable:** Lista anotada de campos con su tipo y posible gráfica asociada.

---

### Fase 2 — Diseño de la Arquitectura Visual (30 min)

#### Layout del Dashboard

```
┌─────────────────────────────────────────────────────────────┐
│  HEADER: Título de la encuesta + Fecha + Total respondentes │
├───────────────┬─────────────────────────────────────────────┤
│  SIDEBAR      │  KPI CARDS (4 métricas clave)               │
│  · Filtros    ├─────────────────────────────────────────────┤
│    por:       │  FILA 1: Gráfica grande (demográfico)       │
│    - Género   ├───────────────┬─────────────────────────────┤
│    - Edad     │  Gráfica 2    │  Gráfica 3                  │
│    - Grupo    ├───────────────┴─────────────────────────────┤
│               │  FILA 2: Gráficas de escalas / satisfacción │
│  · Buscador   ├─────────────────────────────────────────────┤
│    por ID     │  TABLA: Respuestas detalladas (paginada)    │
└───────────────┴─────────────────────────────────────────────┘
```

#### Paleta de Colores (Tema Oscuro Profesional)
```css
--bg-primary:    #0f1117   /* Fondo principal */
--bg-card:       #1a1d27   /* Cards y paneles */
--accent-1:      #6366f1   /* Índigo — acento principal */
--accent-2:      #22d3ee   /* Cyan — acento secundario */
--accent-3:      #f59e0b   /* Amber — destacados */
--text-primary:  #f1f5f9   /* Texto principal */
--text-muted:    #64748b   /* Texto secundario */
```

---

### Fase 3 — Selección de Librerías (Definitivas)

| Librería | CDN | Uso |
|---|---|---|
| **Tailwind CSS v3** | `cdn.tailwindcss.com` | Layout, utilidades, responsive |
| **Chart.js v4** | `cdn.jsdelivr.net` | Barras, líneas, pie, doughnut, radar |
| **ApexCharts v3** | `cdn.jsdelivr.net` | Heatmaps, treemaps, sparklines |
| **Alpine.js v3** | `cdn.jsdelivr.net` | Reactividad (filtros, toggles) sin framework |
| **Font: DM Sans** | `fonts.googleapis.com` | Tipografía profesional para datos |
| **Lucide Icons** | `unpkg.com/lucide` | Iconografía consistente |

> **¿Por qué esta combinación?**  
> Chart.js cubre el 80% de los casos comunes con excelente rendimiento. ApexCharts añade gráficas más especializadas. Alpine.js hace los filtros interactivos sin necesidad de React/Vue.

---

### Fase 4 — Mapa de Gráficas por Tipo de Dato

#### 🧑‍🤝‍🧑 Datos Demográficos
| Campo | Gráfica Recomendada | Librería |
|---|---|---|
| Género | **Doughnut** con porcentajes | Chart.js |
| Edad | **Histograma** (rangos 18–25, 26–35…) | Chart.js |
| Ciudad / Región | **Bar chart horizontal** ordenado | Chart.js |
| Escolaridad | **Bar chart vertical** | Chart.js |

#### ⭐ Escalas de Valoración (1–5 o 1–10)
| Visualización | Descripción |
|---|---|
| **Gauge / Radial** | Promedio general por pregunta |
| **Stacked Bar** | Distribución de respuestas (1,2,3,4,5) |
| **Radar Chart** | Comparación entre múltiples dimensiones |
| **Heatmap** | Correlación entre escala y demografía |

#### ☑️ Opción Múltiple
| Visualización | Descripción |
|---|---|
| **Bar chart** | Frecuencia de cada opción |
| **Treemap** | Proporción visual de categorías |
| **Word cloud** (opcional) | Si hay opciones abiertas |

#### 📌 KPI Cards (métricas rápidas)
- Total de respondentes
- Promedio general de satisfacción (si aplica)
- % de completitud
- Métrica más relevante del tema específico

---

### Fase 5 — Implementación (Orden de Construcción)

```
1. [ ] Estructura HTML base con Tailwind (layout grid/flex)
2. [ ] Carga del JSON con fetch() + manejo de errores
3. [ ] Funciones de procesamiento de datos:
       - calcularFrecuencias(campo)
       - calcularPromedios(campo)
       - agruparPorDemografia(campo, filtro)
4. [ ] Render de KPI Cards
5. [ ] Gráficas demográficas (Chart.js)
6. [ ] Gráficas de escalas (Chart.js + ApexCharts)
7. [ ] Gráficas de opción múltiple
8. [ ] Sistema de filtros reactivos (Alpine.js)
9. [ ] Tabla de datos detallada con paginación
10.[ ] Animaciones de entrada (CSS transitions)
11.[ ] Responsive mobile (breakpoints Tailwind)
12.[ ] Botón de exportar a PNG (Chart.js built-in)
```

---

### Fase 6 — Funcionalidades Interactivas

| Feature | Implementación |
|---|---|
| **Filtros por demografía** | Alpine.js `x-data` + re-render de charts |
| **Tooltips en gráficas** | Chart.js tooltip callbacks |
| **Dark/Light mode** | Tailwind `dark:` + toggle button |
| **Exportar gráfica** | `chart.toBase64Image()` → descarga PNG |
| **Tabla búsqueda** | Filtro JS sobre array de respuestas |
| **Animación de números** | Counter animation en KPI Cards |

---

### Fase 7 — Estructura del Código JS

```javascript
// Arquitectura sugerida dentro del <script>

// 1. CARGA DE DATOS
const data = await fetch('./data.json').then(r => r.json());

// 2. PROCESAMIENTO
const stats = {
  total: data.length,
  porGenero: calcularFrecuencias(data, 'genero'),
  porEdad:   calcularRangos(data, 'edad', [18,25,35,45,60]),
  promedios: calcularPromedios(data, ['p1','p2','p3']),
  // ...
};

// 3. RENDER
renderKPIs(stats);
renderCharts(stats);
renderTabla(data);

// 4. FILTROS
function aplicarFiltros(filtros) {
  const filtrado = data.filter(r =>
    (!filtros.genero || r.genero === filtros.genero) &&
    (!filtros.edad   || enRango(r.edad, filtros.edad))
  );
  renderCharts(procesarDatos(filtrado));
}
```

---

## ✅ Checklist Final Antes de Presentar

- [ ] ¿Carga correctamente con el JSON real?
- [ ] ¿Los filtros actualizan todas las gráficas?
- [ ] ¿Se ve bien en pantalla de proyector (1920×1080)?
- [ ] ¿Los colores tienen suficiente contraste?
- [ ] ¿Las etiquetas de las gráficas son legibles?
- [ ] ¿El título y fecha son correctos?
- [ ] ¿Funciona sin conexión a internet? (considerar alojar libs localmente)

---

## 🚀 Siguiente Paso

**Comparte tu archivo JSON** y con base en su estructura real se construirá el `index.html` completo con:
- Todas las gráficas mapeadas a tus campos reales
- Funciones de procesamiento adaptadas a tus datos
- Filtros sobre las variables demográficas que tengas
- Diseño final cohesivo y listo para presentar

> 💡 Si el JSON tiene datos sensibles, puedes anonimizar los valores antes de compartirlo — la estructura (claves y tipos de dato) es lo más importante.
