# 📚 Módulo 1: Fundamentos de Modelos de Lenguaje

## 🎯 **Objetivo del Módulo**

Establecer las bases teóricas y prácticas necesarias para comprender el funcionamiento de los modelos de lenguaje modernos, con especial énfasis en los conceptos que sustentan Llama 3.1.

---

## 📖 **Contenido del Módulo**

### 🔤 **1. Tokenización**
- **Concepto**: Conversión de texto en tokens procesables
- **Tipos**: BPE, WordPiece, SentencePiece
- **Práctica**: Implementación con DistilBERT
- **Vocabulario**: Gestión de tokens especiales

### 🎯 **2. Embeddings**
- **Representaciones Vectoriales**: De tokens a vectores densos
- **Dimensionalidad**: Comprensión del espacio semántico
- **Visualización**: Distribuciones y patrones
- **Contexto**: Embeddings contextuales vs estáticos

### 👁️ **3. Mecanismo de Atención**
- **Concepto Fundamental**: Query, Key, Value
- **Implementación Simplificada**: Matrices de atención
- **Visualización**: Heatmaps de atención
- **Multi-Head Attention**: Múltiples perspectivas

### 📊 **4. Evolución de Arquitecturas**
- **N-gram**: Modelos estadísticos tradicionales
- **RNN/LSTM**: Procesamiento secuencial
- **Transformers**: Revolución de la atención
- **Llama 3.1**: Estado del arte actual

### 🛠️ **5. Preprocesamiento de Texto**
- **Limpieza**: Normalización y filtrado
- **Estrategias**: Diferentes enfoques según el caso
- **Tokens Especiales**: PAD, UNK, CLS, SEP, MASK
- **Mejores Prácticas**: Preparación para modelos

---

## 📁 **Archivos del Módulo**

### 📓 **laboratorio-modulo-n1.ipynb**
**Notebook principal con implementaciones prácticas**

#### 🔧 **Clase ConceptosBasicos**
```python
class ConceptosBasicos:
    def demo_tokenizacion(self, texto)
    def demo_embeddings(self, texto)
    def demo_atencion_simple(self, secuencia)
    def demo_comparacion_modelos(self)
    def demo_preprocesamiento_texto(self, texto)
```

#### 🎨 **Visualizaciones Incluidas**
- **Distribución de embeddings**: Histogramas y heatmaps
- **Matrices de atención**: Visualización interactiva
- **Evolución de modelos**: Gráficos comparativos
- **Estadísticas de tokens**: Análisis cuantitativo

### 🎮 **demo_atencion.ipynb**
**Demostración interactiva del mecanismo de atención**

#### ✨ **Características**
- **Widgets interactivos**: Jupyter widgets para exploración
- **Visualización en tiempo real**: Cambios dinámicos
- **Múltiples ejemplos**: Diferentes tipos de secuencias
- **Explicaciones paso a paso**: Comprensión profunda

---

## 🚀 **Inicio Rápido**

### 1️⃣ **Prerrequisitos**
```bash
pip install torch transformers matplotlib seaborn numpy
```

### 2️⃣ **Ejecutar Laboratorio Principal**
```bash
jupyter lab laboratorio-modulo-n1.ipynb
```

### 3️⃣ **Explorar Demo Interactiva**
```bash
jupyter lab demo_atencion.ipynb
```

---

## 🎓 **Objetivos de Aprendizaje**

Al completar este módulo, los participantes podrán:

### ✅ **Conocimientos Teóricos**
- Explicar el proceso de tokenización y su importancia
- Describir cómo funcionan los embeddings contextuales
- Comprender el mecanismo de atención en detalle
- Comparar diferentes arquitecturas de modelos de lenguaje

### ✅ **Habilidades Prácticas**
- Implementar tokenización básica con Transformers
- Generar y visualizar embeddings
- Crear matrices de atención simples
- Preprocesar texto para modelos de lenguaje

### ✅ **Aplicación Gubernamental**
- Identificar casos de uso apropiados para cada técnica
- Evaluar requisitos de preprocesamiento para datos oficiales
- Comprender limitaciones y consideraciones de privacidad

---

## 🔍 **Conceptos Clave**

### 🧠 **Fundamentos Técnicos**
- **Tokenización**: `texto → tokens → IDs`
- **Embeddings**: `tokens → vectores densos`
- **Atención**: `Q × K^T → pesos → V`
- **Contexto**: Información bidireccional

### 📈 **Métricas Importantes**
- **Tamaño de vocabulario**: ~30K-100K tokens
- **Dimensión de embeddings**: 512-4096
- **Longitud de contexto**: 512-128K tokens
- **Parámetros del modelo**: 7B-70B+

---

## 🛠️ **Ejercicios Prácticos**

### 🔤 **Ejercicio 1: Tokenización Personalizada**
```python
# Comparar diferentes tokenizers
tokenizers = ["bert-base", "gpt2", "llama"]
texto = "Gobierno de Argentina implementa IA"
# Analizar diferencias en tokenización
```

### 🎯 **Ejercicio 2: Visualización de Embeddings**
```python
# Crear embeddings para términos gubernamentales
terminos = ["ciudadano", "servicio", "digital", "transparencia"]
# Visualizar similitudes semánticas
```

### 👁️ **Ejercicio 3: Atención en Contexto**
```python
# Analizar atención en frases oficiales
frase = "El Ministerio anuncia nueva política digital"
# Identificar qué palabras reciben más atención
```

---

## 📊 **Evaluación del Módulo**

### ✅ **Criterios de Completitud**
- [ ] Ejecutar todos los notebooks sin errores
- [ ] Completar ejercicios prácticos
- [ ] Generar visualizaciones correctas
- [ ] Responder preguntas conceptuales

### 🎯 **Preguntas de Reflexión**
1. ¿Cómo afecta la tokenización a idiomas con acentos?
2. ¿Qué ventajas tienen los embeddings contextuales?
3. ¿Por qué es importante el mecanismo de atención?
4. ¿Cómo elegir el preprocesamiento adecuado?

---

## 🔗 **Recursos Adicionales**

### 📚 **Lecturas Recomendadas**
- [Attention Is All You Need](https://arxiv.org/abs/1706.03762)
- [BERT: Pre-training of Deep Bidirectional Transformers](https://arxiv.org/abs/1810.04805)
- [The Illustrated Transformer](http://jalammar.github.io/illustrated-transformer/)

### 🎥 **Videos Educativos**
- [3Blue1Brown: Attention in Transformers](https://www.youtube.com/watch?v=eMlx5fFNoYc)
- [Andrej Karpathy: Let's build GPT](https://www.youtube.com/watch?v=kCc8FmEb1nY)

### 🛠️ **Herramientas**
- [Hugging Face Tokenizers](https://huggingface.co/docs/tokenizers/)
- [BertViz](https://github.com/jessevig/bertviz) - Visualización de atención
- [Transformers Interpret](https://github.com/cdpierse/transformers-interpret)

---

## ⏱️ **Tiempo Estimado**

- **Lectura de conceptos**: 45 minutos
- **Laboratorio principal**: 90 minutos
- **Demo interactiva**: 30 minutos
- **Ejercicios adicionales**: 45 minutos
- **Total**: **3-4 horas**

---

## ➡️ **Siguiente Paso**

Una vez completado este módulo, continúa con:
**[Módulo 2: Introducción a Llama 3.1](../módulo%202/README.md)**

---

**¡Construyamos juntos las bases sólidas para la IA gubernamental! 🏛️🤖**
