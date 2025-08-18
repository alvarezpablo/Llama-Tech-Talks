# Módulo 5 – RAG con Ollama

## Contenido
- rag_ollama_example.ipynb: Implementación completa de RAG (Retrieval-Augmented Generation) usando Ollama

## Objetivos
- Implementar un sistema RAG funcional
- Integrar Llama 3.1 con bases de conocimiento externas
- Usar Ollama para ejecutar modelos localmente

## Requisitos

### Software
- Python 3.10+
- Ollama instalado localmente
- Jupyter Lab/Notebook

### Instalación de Ollama
1. **Windows/Mac/Linux**: Descarga desde https://ollama.ai
2. **Verificar instalación**: `ollama --version`
3. **Descargar Llama 3.1**: `ollama pull llama3.1`

### Dependencias Python
```bash
pip install ollama langchain langchain-community faiss-cpu sentence-transformers
pip install numpy pandas matplotlib requests beautifulsoup4
```

## Ejecución rápida
1. **Iniciar Ollama**:
   ```bash
   ollama serve
   ```
2. **En otra terminal, verificar que Llama 3.1 está disponible**:
   ```bash
   ollama list
   ```
3. **Abrir Jupyter Lab**: `jupyter lab`
4. **Ejecutar el notebook**: rag_ollama_example.ipynb

## Componentes del RAG
- **Retrieval**: Búsqueda de documentos relevantes usando embeddings
- **Augmentation**: Enriquecimiento del prompt con contexto recuperado
- **Generation**: Generación de respuesta usando Llama 3.1

## Casos de uso
- Chatbot con conocimiento específico de empresa
- Asistente de documentación técnica
- Sistema de preguntas y respuestas sobre corpus de texto

## Notas
- El notebook incluye ejemplos con documentos de muestra
- Puedes reemplazar los documentos con tu propio corpus
- Tiempo estimado: 20-30 minutos
- Ollama debe estar ejecutándose en background durante todo el proceso
