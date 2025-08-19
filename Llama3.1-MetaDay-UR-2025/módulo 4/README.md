# Módulo 4 – Fine-tuning con QLoRA

## Contenido
- **🆕 Llama3.1_Unsloth_FineTuning_Optimizado.ipynb**: **RECOMENDADO** - Fine-tuning ultra-eficiente con Unsloth (2x más rápido, 60% menos memoria)
- **🔗 RAG_Modelo_Optimizado_Unsloth.ipynb**: **RAG SIN OLLAMA** - Sistema RAG completo usando directamente el modelo optimizado
- **🎯 Evaluacion_Modelo_Optimizado_Simple.ipynb**: **SIN CONFLICTOS** - Evaluación directa sin instalaciones, evita errores PyTorch/torchaudio
- **⚡ Evaluacion_Optimizada_Modelo_HF.ipynb**: **EVALUACIÓN CON TU CÓDIGO OPTIMIZADO** - Usa FastLanguageModel.for_inference() y chat templates optimizados
- **🧪 Probar_Modelo_FineTuneado_HuggingFace.ipynb**: **EVALUACIÓN COMPLETA** - Tests comprehensivos del modelo `alvarezpablo/llama3.1-8b-finetune-metaday`
- **🔧 Solucion_Errores_Comunes.ipynb**: **EJECUTAR PRIMERO SI HAY ERRORES** - Soluciones para protobuf, CUDA, instalación, etc.
- **🔗 Usar_Modelo_FineTuneado_con_Ollama.ipynb**: Cómo usar tu modelo fine-tuneado con Ollama (conexión con Módulo 5)
- Ejemplo_Qlora_cpu_with_outputs.ipynb: Fine-tuning QLoRA optimizado para CPU con salidas incluidas
- Ejemplo_Qlora_gpu_A100_no_outputs.ipynb: Fine-tuning QLoRA para GPU A100 (sin salidas pre-ejecutadas)

## Objetivos
- Aprender técnicas de fine-tuning eficiente con QLoRA y **Unsloth**
- Implementar **Rank-Stabilized LoRA (rsLoRA)** para mejor estabilidad
- Usar datasets de ultra alta calidad (**FineTome-100k**)
- Optimizar hiperparámetros basados en mejores prácticas
- Comparar rendimiento entre CPU y GPU
- Exportar modelos a múltiples formatos (LoRA, merged, GGUF)

## Requisitos

### Para CPU (Ejemplo_Qlora_cpu_with_outputs.ipynb)
- Python 3.10+
- Al menos 16GB RAM recomendado
- Dependencias:
  ```bash
  pip install torch transformers datasets peft bitsandbytes accelerate
  ```

### Para GPU (Ejemplo_Qlora_gpu_A100_no_outputs.ipynb)
- GPU con al menos 16GB VRAM (A100, V100, RTX 4090, etc.)
- CUDA 11.8+ o 12.x
- Dependencias:
  ```bash
  pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
  pip install transformers datasets peft bitsandbytes accelerate
  ```

## Ejecución rápida

### 🔧 PASO 0: Si tienes errores (EJECUTAR PRIMERO)
1. Abre `Solucion_Errores_Comunes.ipynb`
2. **Errores cubiertos**: TypeError protobuf, CUDA out of memory, ImportError unsloth, device errors
3. **Soluciones automáticas**: Instalación limpia, configuración preventiva, diagnóstico completo
4. **Tiempo**: 5-10 minutos para resolver la mayoría de problemas

### 🎯 OPCIÓN RECOMENDADA: Sin Conflictos de Dependencias
1. Abre `Evaluacion_Modelo_Optimizado_Simple.ipynb`
2. **Sin instalaciones**: Usa dependencias existentes, evita conflictos PyTorch/torchaudio/fastai
3. **Tu código optimizado**: FastLanguageModel + chat templates + use_cache=True
4. **Modelo pre-optimizado**: Ya tiene optimizaciones Unsloth del fine-tuning
5. **Tests focalizados**: Verificación rápida + tests extendidos opcionales
6. **Tiempo estimado**: 5-10 min para verificación, 15-20 min completo

### 🔗 OPCIÓN RAG OPTIMIZADO: Sin Ollama
1. Abre `RAG_Modelo_Optimizado_Unsloth.ipynb`
2. **Sistema RAG completo**: Retrieval + Generation con tu modelo optimizado
3. **Sin Ollama**: Usa directamente el modelo Unsloth + HuggingFace embeddings
4. **Ventajas**: 2-3x más rápido, control total, sin dependencias externas
5. **Dataset incluido**: Chistes en español para demostración
6. **Tiempo estimado**: 20-30 min para setup completo + tests

### 🚀 Opción FINE-TUNING: Unsloth Optimizado
1. Abre `Llama3.1_Unsloth_FineTuning_Optimizado.ipynb`
2. **Ventajas**: 2x más rápido, 60% menos memoria, técnicas state-of-the-art
3. Funciona en GPU T4/A100 y CPU (aunque más lento)
4. Tiempo estimado: 20-30 min para 10k muestras en T4
5. Incluye exportación a GGUF para Ollama/LM Studio
6. **Después del fine-tuning**: Ejecuta `Usar_Modelo_FineTuneado_con_Ollama.ipynb` para usar tu modelo localmente

### ⚡ Opción EVALUACIÓN OPTIMIZADA: Tu Código Mejorado
1. Abre `Evaluacion_Optimizada_Modelo_HF.ipynb`
2. **Usa tu código optimizado**: FastLanguageModel.for_inference(), chat templates mejorados
3. **Velocidad 2x más rápida**: use_cache=True, decodificación eficiente
4. **Tests focalizados**: 20 tests en 5 categorías principales
5. **Visualización en tiempo real**: TextStreamer para ver respuestas generándose
6. **Tiempo estimado**: 10-15 min para evaluación completa

### 🧪 Opción EVALUACIÓN COMPLETA: Probar Modelo desde Hugging Face
1. Abre `Probar_Modelo_FineTuneado_HuggingFace.ipynb`
2. **Modelo pre-cargado**: `alvarezpablo/llama3.1-8b-finetune-metaday`
3. **8 suites de tests**: Matemáticas, conversación, programación, conocimiento, idiomas, creatividad, análisis, casos edge
4. **56 tests únicos** con métricas automáticas de calidad
5. **Exportación completa**: JSON, CSV, y reporte markdown
6. **Tiempo estimado**: 15-25 min para evaluación completa

### Opción 3: CPU (más lento pero accesible)
1. Abre `Ejemplo_Qlora_cpu_with_outputs.ipynb`
2. Este notebook ya tiene salidas pre-ejecutadas para referencia
3. Puedes ejecutar celdas individuales o todo el notebook

### Opción 4: GPU A100 (método tradicional)
1. Verifica que tienes GPU disponible: `nvidia-smi`
2. Abre `Ejemplo_Qlora_gpu_A100_no_outputs.ipynb`
3. Ejecuta las celdas en orden
4. Tiempo estimado: 30-60 minutos dependiendo del dataset

## Alternativas en la nube
- Google Colab Pro (GPU T4/A100)
- Kaggle Notebooks (GPU P100/T4)
- AWS SageMaker, Azure ML, GCP Vertex AI

## Notas importantes
- **Unsloth** ofrece las mejores optimizaciones disponibles actualmente
- **rsLoRA** mejora la estabilidad del entrenamiento con ranks altos
- **FineTome-100k** es un dataset de ultra alta calidad filtrado con clasificadores educativos
- QLoRA reduce significativamente el uso de memoria comparado con fine-tuning completo
- Los ejemplos usan modelos pequeños para demostración; en producción usa modelos más grandes
- Ajusta `max_steps`, `batch_size` según tu hardware disponible

## Nuevas características implementadas
- ✅ **Unsloth**: 2x más rápido, 60% menos memoria
- ✅ **rsLoRA**: Rank-Stabilized LoRA para mejor estabilidad
- ✅ **Chat templates**: ChatML optimizado para conversaciones
- ✅ **Dataset de calidad**: FineTome-100k filtrado
- ✅ **Hiperparámetros optimizados**: Basados en investigación reciente
- ✅ **Exportación múltiple**: LoRA, merged, GGUF
- ✅ **AdamW 8-bit**: Optimizador eficiente en memoria
- ✅ **Evaluación comprehensiva**: 56 tests en 8 categorías diferentes
- ✅ **Métricas automáticas**: Velocidad, calidad, completitud, estructura
- ✅ **Código optimizado validado**: FastLanguageModel.for_inference() + chat templates
- ✅ **Evaluación en tiempo real**: TextStreamer para visualización inmediata
- ✅ **RAG optimizado**: Sistema completo sin Ollama, 2-3x más rápido
- ✅ **Embeddings locales**: HuggingFace multilingüe en lugar de Ollama
