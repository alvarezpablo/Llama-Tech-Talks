# Módulo 4 – Fine-tuning con QLoRA

## Contenido
- **🆕 Llama3.1_Unsloth_FineTuning_Optimizado.ipynb**: **RECOMENDADO** - Fine-tuning ultra-eficiente con Unsloth (2x más rápido, 60% menos memoria)
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

### 🚀 Opción RECOMENDADA: Unsloth Optimizado
1. Abre `Llama3.1_Unsloth_FineTuning_Optimizado.ipynb`
2. **Ventajas**: 2x más rápido, 60% menos memoria, técnicas state-of-the-art
3. Funciona en GPU T4/A100 y CPU (aunque más lento)
4. Tiempo estimado: 20-30 min para 10k muestras en T4
5. Incluye exportación a GGUF para Ollama/LM Studio
6. **Después del fine-tuning**: Ejecuta `Usar_Modelo_FineTuneado_con_Ollama.ipynb` para usar tu modelo localmente

### Opción 2: CPU (más lento pero accesible)
1. Abre `Ejemplo_Qlora_cpu_with_outputs.ipynb`
2. Este notebook ya tiene salidas pre-ejecutadas para referencia
3. Puedes ejecutar celdas individuales o todo el notebook

### Opción 3: GPU A100 (método tradicional)
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
