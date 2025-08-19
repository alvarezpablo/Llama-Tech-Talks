# Módulo 1 – Fundamentos y Atención

## Contenido
- **🎯 demo_atencion.ipynb**: **ACTUALIZADO** - Demostración interactiva avanzada de mecanismos de atención con visualizaciones mejoradas
- laboratorio-modulo-n1.ipynb: Ejercicios prácticos de fundamentos y atención

## Objetivos
- Entender el mecanismo de atención a alto nivel
- Manipular parámetros simples y observar su impacto
- **🆕 Visualizar matrices de atención** con gráficos interactivos
- **🆕 Explorar diferentes capas y cabezas** de atención
- **🆕 Analizar patrones de atención** en modelos BERT en español

## 🆕 Nuevas Características del Demo de Atención

### 🎨 Visualizaciones Avanzadas:
- **📊 Gráficos de barras interactivos** - Visualizar scores de atención por token
- **🔗 Diagramas de líneas de atención** - Conexiones visuales entre tokens
- **🎯 Visualización ultra-wide** - Formato optimizado para análisis detallado
- **🌈 Mapas de calor con colores** - Intensidad de atención con escala de colores

### 🎛️ Controles Interactivos:
- **Selector de capas** - Explorar diferentes niveles del modelo
- **Selector de cabezas** - Analizar múltiples cabezas de atención
- **Selector de tokens** - Investigar atención desde cualquier token
- **Umbral configurable** - Filtrar conexiones de baja intensidad

### 📈 Funcionalidades Técnicas:
- **Extracción de matrices de atención** de modelos BERT
- **Análisis cuantitativo** con valores numéricos precisos
- **Normalización automática** de scores de atención
- **Resaltado inteligente** de tokens origen y destino más relevantes

## Requisitos
- Python 3.10+
- Jupyter Lab/Notebook
- **🆕 Widgets interactivos** para controles avanzados

## Ejecución rápida

### 🎯 Demo de Atención Interactivo (RECOMENDADO):
1. Abre `demo_atencion.ipynb`
2. **Características**: Visualizaciones interactivas, múltiples tipos de gráficos, controles de widgets
3. **Modelos**: BERT en español para análisis de atención
4. **Tiempo estimado**: 10-15 minutos para exploración completa

### 📚 Laboratorio Práctico:
1. Abre `laboratorio-modulo-n1.ipynb`
2. Ejercicios paso a paso sobre fundamentos
3. Tiempo estimado: 20-30 minutos

## Instalación de Dependencias

```bash
# Dependencias básicas
pip install torch transformers

# Visualizaciones avanzadas
pip install matplotlib seaborn

# Widgets interactivos (NUEVO)
pip install ipywidgets

# Para Jupyter Lab (si usas JupyterLab)
jupyter labextension install @jupyter-widgets/jupyterlab-manager
```

## 🎮 Cómo Usar las Nuevas Funcionalidades

### 1. Visualización Básica de Atención:
- Ejecuta las celdas hasta llegar a los widgets
- Usa los sliders para cambiar capa, cabeza y token
- Observa cómo cambian los patrones de atención

### 2. Análisis Avanzado:
- **plot_attention()**: Gráfico de barras tradicional
- **plot_attention_lines_ultra_wide()**: Visualización con líneas de conexión
- Ajusta el parámetro `thresh` para filtrar conexiones débiles

### 3. Interpretación de Resultados:
- **Líneas gruesas**: Mayor atención entre tokens
- **Colores intensos**: Scores de atención altos
- **Tokens resaltados**: Origen (azul) y destino principal (rojo)
- **Valores numéricos**: Scores exactos de atención

## 💡 Tips para el Análisis:
- Prueba diferentes capas (0-11) para ver evolución de patrones
- Compara múltiples cabezas en la misma capa
- Analiza tokens de función vs. tokens de contenido
- Observa patrones de auto-atención vs. atención cruzada

## 🔍 Casos de Uso Educativos:
- **Demostrar conceptos** de atención en transformers
- **Analizar comportamiento** de modelos pre-entrenados
- **Comparar estrategias** de diferentes cabezas de atención
- **Entender relaciones** sintácticas y semánticas

