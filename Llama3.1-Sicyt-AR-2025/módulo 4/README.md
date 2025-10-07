# ⚡ Módulo 4: Optimización y Fine-tuning

## 🎯 **Objetivo del Módulo**

Dominar técnicas avanzadas de optimización, fine-tuning y sistemas RAG para crear soluciones de IA especializadas y eficientes para aplicaciones gubernamentales específicas.

---

## 🚀 **Contenido Avanzado del Módulo**

### ⚡ **Técnicas de Optimización**
- **Unsloth**: Framework ultra-eficiente para fine-tuning
- **QLoRA**: Quantized Low-Rank Adaptation
- **rsLoRA**: Rank-Stabilized LoRA
- **Sistemas RAG**: Retrieval-Augmented Generation

### 🏛️ **Aplicaciones Gubernamentales**
- **Modelos especializados**: Adaptados a terminología oficial
- **Bases de conocimiento**: RAG con documentos gubernamentales
- **Eficiencia operativa**: Optimización para servidores limitados
- **Evaluación rigurosa**: Métricas de calidad y rendimiento

---

## 📁 **Notebooks del Módulo**

### ⚡ **Llama3.1_Unsloth_FineTuning_Optimizado.ipynb**
**Fine-tuning ultra-eficiente con Unsloth**

#### 🎯 **Características Principales**
- **2x más rápido** que métodos tradicionales
- **60% menos uso de memoria**
- **Rank-Stabilized LoRA (rsLoRA)**
- **Chat templates optimizados**
- **Configuración automática de hiperparámetros**

#### 🔧 **Implementación**
```python
from unsloth import FastLanguageModel
import torch

# Cargar modelo con Unsloth
model, tokenizer = FastLanguageModel.from_pretrained(
    model_name="unsloth/llama-3.1-8b-bnb-4bit",
    max_seq_length=2048,
    dtype=None,
    load_in_4bit=True,
)

# Configurar LoRA
model = FastLanguageModel.get_peft_model(
    model,
    r=16,  # Rank
    target_modules=["q_proj", "k_proj", "v_proj", "o_proj"],
    lora_alpha=16,
    lora_dropout=0,
    bias="none",
    use_gradient_checkpointing="unsloth",
    random_state=3407,
    use_rslora=True,  # Rank Stabilized LoRA
)
```

### 🔍 **RAG_Modelo_Optimizado_Unsloth.ipynb**
**Sistema RAG con modelo optimizado**

#### 🎯 **Ventajas de esta Implementación**
- **Modelo pre-optimizado**: Ya tiene optimizaciones Unsloth
- **Sin dependencias externas**: No necesita Ollama corriendo
- **Control total**: Acceso directo al modelo y parámetros
- **Embeddings locales**: Usa sentence-transformers

#### 🔧 **Arquitectura RAG**
```python
# 1. Base de datos vectorial
from langchain_chroma import Chroma
from sentence_transformers import SentenceTransformer

# 2. Modelo de embeddings
embedding_model = SentenceTransformer('all-MiniLM-L6-v2')

# 3. Modelo optimizado para generación
model = FastLanguageModel.for_inference(model)

# 4. Pipeline RAG completo
def rag_query(question, context_docs):
    # Recuperar documentos relevantes
    relevant_docs = retrieve_documents(question, context_docs)
    
    # Generar respuesta con contexto
    prompt = f"Contexto: {relevant_docs}\nPregunta: {question}\nRespuesta:"
    response = model.generate(prompt)
    return response
```

### 📊 **Evaluacion_Modelo_Optimizado_Simple.ipynb**
**Evaluación sistemática de modelos fine-tuneados**

#### 🔍 **Métricas de Evaluación**
- **BLEU Score**: Calidad de generación
- **ROUGE**: Resumen y extracción
- **Perplexity**: Fluidez del lenguaje
- **Tiempo de respuesta**: Eficiencia operativa
- **Uso de memoria**: Recursos consumidos

### 🛠️ **Solucion_Errores_Comunes.ipynb**
**Troubleshooting y mejores prácticas**

#### ❌ **Problemas Frecuentes**
- **CUDA out of memory**: Soluciones de memoria
- **Convergencia lenta**: Ajuste de hiperparámetros
- **Overfitting**: Técnicas de regularización
- **Incompatibilidades**: Versiones y dependencias

### 🔄 **Usar_Modelo_FineTuneado_con_Ollama.ipynb**
**Integración de modelos fine-tuneados con Ollama**

#### 🔧 **Proceso de Integración**
1. **Exportar modelo**: Formato compatible con Ollama
2. **Crear Modelfile**: Configuración personalizada
3. **Importar a Ollama**: `ollama create`
4. **Desplegar**: Uso en producción

### 💻 **Ejemplo_Qlora_gpu_A100_no_outputs.ipynb**
**QLoRA optimizado para GPUs A100**

#### ⚡ **Optimizaciones A100**
- **Precision mixta**: FP16/BF16
- **Gradient checkpointing**: Memoria eficiente
- **DataLoader optimizado**: Máximo throughput
- **Multi-GPU**: Paralelización avanzada

---

## 🎯 **Fine-tuning para Casos Gubernamentales**

### 📋 **1. Dataset de Atención Ciudadana**
```python
# Ejemplo de datos de entrenamiento
training_data = [
    {
        "instruction": "¿Cómo tramito mi DNI?",
        "input": "",
        "output": "Para tramitar tu DNI debes: 1) Solicitar turno online en argentina.gob.ar..."
    },
    {
        "instruction": "Requisitos para pasaporte",
        "input": "",
        "output": "Los requisitos para el pasaporte argentino son: 1) DNI vigente..."
    }
]

# Formato para fine-tuning
def format_prompt(example):
    return f"""### Consulta Ciudadana:
{example['instruction']}

### Respuesta Oficial:
{example['output']}"""
```

### 📄 **2. Análisis de Documentos Oficiales**
```python
# Dataset especializado en documentos gubernamentales
document_data = [
    {
        "document": "Decreto 123/2024 sobre digitalización...",
        "summary": "El decreto establece lineamientos para la transformación digital...",
        "key_points": ["Digitalización obligatoria", "Plazos de implementación"]
    }
]
```

### 🌐 **3. Traducción de Comunicados**
```python
# Dataset multilingüe para comunicación oficial
translation_data = [
    {
        "spanish": "El Ministerio anuncia nueva política digital",
        "english": "The Ministry announces new digital policy",
        "context": "official_communication"
    }
]
```

---

## 🔧 **Configuración de Entrenamiento**

### ⚙️ **Hiperparámetros Optimizados**
```python
from transformers import TrainingArguments

training_args = TrainingArguments(
    output_dir="./llama-3.1-gobierno-ar",
    num_train_epochs=3,
    per_device_train_batch_size=4,
    gradient_accumulation_steps=4,
    warmup_steps=100,
    learning_rate=2e-4,
    fp16=True,
    logging_steps=10,
    save_strategy="epoch",
    evaluation_strategy="epoch",
    load_best_model_at_end=True,
    metric_for_best_model="eval_loss",
    greater_is_better=False,
)
```

### 🎯 **LoRA Configuration**
```python
from peft import LoraConfig

lora_config = LoraConfig(
    r=16,                    # Rank
    lora_alpha=32,          # Scaling factor
    target_modules=[        # Módulos objetivo
        "q_proj", "k_proj", "v_proj", "o_proj",
        "gate_proj", "up_proj", "down_proj"
    ],
    lora_dropout=0.1,       # Dropout para regularización
    bias="none",            # Sin bias en adaptadores
    task_type="CAUSAL_LM"   # Tipo de tarea
)
```

---

## 🔍 **Sistema RAG Gubernamental**

### 📚 **Base de Conocimiento**
```python
# Documentos gubernamentales para RAG
knowledge_base = [
    "Constitución Nacional Argentina",
    "Código Civil y Comercial",
    "Decretos y resoluciones ministeriales",
    "Manuales de procedimientos",
    "Guías de trámites ciudadanos"
]

# Procesamiento de documentos
def process_documents(docs):
    chunks = []
    for doc in docs:
        # Dividir en chunks semánticamente coherentes
        doc_chunks = split_document(doc, chunk_size=512)
        chunks.extend(doc_chunks)
    return chunks
```

### 🔍 **Retrieval Optimizado**
```python
from sentence_transformers import SentenceTransformer
import faiss
import numpy as np

class GovernmentRAG:
    def __init__(self, documents):
        self.embedding_model = SentenceTransformer('all-MiniLM-L6-v2')
        self.documents = documents
        self.embeddings = self.embedding_model.encode(documents)
        
        # Índice FAISS para búsqueda eficiente
        self.index = faiss.IndexFlatIP(self.embeddings.shape[1])
        self.index.add(self.embeddings.astype('float32'))
    
    def retrieve(self, query, k=3):
        query_embedding = self.embedding_model.encode([query])
        scores, indices = self.index.search(query_embedding.astype('float32'), k)
        return [self.documents[i] for i in indices[0]]
    
    def generate_answer(self, question):
        # Recuperar documentos relevantes
        relevant_docs = self.retrieve(question)
        
        # Crear prompt con contexto
        context = "\n".join(relevant_docs)
        prompt = f"""Basándote en la siguiente información oficial:

{context}

Responde a la pregunta: {question}

Respuesta:"""
        
        # Generar respuesta con modelo fine-tuneado
        return self.model.generate(prompt)
```

---

## 📊 **Evaluación y Métricas**

### 🔍 **Métricas de Calidad**
```python
from evaluate import load

# Métricas automáticas
bleu = load("bleu")
rouge = load("rouge")
bertscore = load("bertscore")

def evaluate_model(predictions, references):
    results = {}
    
    # BLEU Score
    results['bleu'] = bleu.compute(
        predictions=predictions, 
        references=references
    )
    
    # ROUGE Score
    results['rouge'] = rouge.compute(
        predictions=predictions, 
        references=references
    )
    
    # BERTScore
    results['bertscore'] = bertscore.compute(
        predictions=predictions, 
        references=references, 
        lang="es"
    )
    
    return results
```

### ⚡ **Métricas de Rendimiento**
```python
import time
import psutil

def benchmark_model(model, test_prompts):
    metrics = {
        'response_times': [],
        'memory_usage': [],
        'tokens_per_second': []
    }
    
    for prompt in test_prompts:
        start_time = time.time()
        start_memory = psutil.virtual_memory().used
        
        # Generar respuesta
        response = model.generate(prompt)
        
        end_time = time.time()
        end_memory = psutil.virtual_memory().used
        
        # Calcular métricas
        response_time = end_time - start_time
        memory_used = end_memory - start_memory
        tokens_generated = len(response.split())
        tokens_per_sec = tokens_generated / response_time
        
        metrics['response_times'].append(response_time)
        metrics['memory_usage'].append(memory_used)
        metrics['tokens_per_second'].append(tokens_per_sec)
    
    return {
        'avg_response_time': np.mean(metrics['response_times']),
        'avg_memory_usage': np.mean(metrics['memory_usage']),
        'avg_tokens_per_second': np.mean(metrics['tokens_per_second'])
    }
```

---

## 🏛️ **Casos de Uso Especializados**

### 📋 **1. Asistente Legal Gubernamental**
```python
# Fine-tuning para consultas legales
legal_assistant = FineTunedModel(
    base_model="llama-3.1-8b",
    dataset="legal_documents_argentina",
    specialization="legal_consultation"
)

# Uso
consulta = "¿Cuáles son los plazos para recurrir una resolución administrativa?"
respuesta = legal_assistant.generate(consulta)
```

### 📊 **2. Análisis de Políticas Públicas**
```python
# RAG especializado en políticas
policy_rag = GovernmentRAG(
    documents=load_policy_documents(),
    specialization="policy_analysis"
)

# Análisis
politica = "Política Nacional de Datos Abiertos"
analisis = policy_rag.analyze_policy(politica)
```

### 🌐 **3. Comunicación Multilingüe**
```python
# Modelo especializado en comunicación oficial
multilingual_model = FineTunedModel(
    base_model="llama-3.1-8b",
    dataset="official_communications_multilingual",
    languages=["es", "en", "pt"]
)

# Traducción oficial
comunicado_es = "El gobierno anuncia nuevas medidas económicas"
comunicado_en = multilingual_model.translate(comunicado_es, target="en")
```

---

## ⏱️ **Tiempo Estimado**

- **Setup y configuración**: 60 minutos
- **Fine-tuning básico**: 120 minutos
- **Sistema RAG**: 90 minutos
- **Evaluación y optimización**: 60 minutos
- **Casos de uso avanzados**: 90 minutos
- **Total**: **6-8 horas**

---

## 🔧 **Requisitos de Hardware**

### 💻 **Para Fine-tuning**
- **GPU**: NVIDIA con 16GB+ VRAM (A100 recomendado)
- **RAM**: 32GB+ sistema
- **Almacenamiento**: 100GB+ SSD

### 🔍 **Para RAG**
- **GPU**: 8GB+ VRAM (opcional)
- **RAM**: 16GB+ sistema
- **Almacenamiento**: 50GB+ para embeddings

---

## ➡️ **Próximos Pasos**

Después de completar este módulo:
1. **Desarrollar proyecto final**: Aplicar técnicas a caso real
2. **Preparar presentación**: Para Semana de la IA 2025
3. **Planificar implementación**: Despliegue en producción
4. **Documentar resultados**: Compartir con comunidad

---

**¡Domina las técnicas más avanzadas de IA para transformar el gobierno! 🏛️⚡**
