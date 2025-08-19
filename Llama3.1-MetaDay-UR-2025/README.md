# Llama 3.1 – Meta Day Uruguay (19 de agosto de 2025)

Este directorio contiene el material de apoyo para la charla/taller de Meta Day en Uruguay sobre Llama 3.1.

## Estructura
- módulo 1: Fundamentos y atención (demo + laboratorio)
- módulo 2: Laboratorio módulo 2
- módulo 3: Laboratorio módulo 3
- módulo 4: Fine-tuning con QLoRA y Unsloth (CPU/GPU) + evaluación + RAG (sin Ollama u Ollama, opcional)

## Diapositivas (PDF)
- Módulo 1: [Módulo 1 - Fundamentos de Llama 3.1 y Transformers](./módulo%201/M%C3%B3dulo%201%20-%20Fundamentos%20de%20Llama%203.1%20y%20Transformers.pdf)
- Módulo 2: [Módulo 2 - Configuración de Entorno](./módulo%202/M%C3%B3dulo%202%20-%20Configuraci%C3%B3n%20de%20Entorno.pdf)
- Módulo 3: [Módulo 3 - Deployment de Ollama](./módulo%203/M%C3%B3dulo%203%20-%20Deployment%20de%20Ollama.pdf)
- Módulo 4: [Módulo 4 - Tecnicas-Avanzadas-de-Fine-Tuning-LLaMA-31](./módulo%204/M%C3%B3dulo%204%20-%20Tecnicas-Avanzadas-de-Fine-Tuning-LLaMA-31.pdf)

## Requisitos generales
- Python 3.10+ recomendado
- Jupyter Lab o Jupyter Notebook
- pip y virtualenv/conda para aislar dependencias
- Git (opcional, para clonar el repo)

## Configuración rápida (local)
1. Crear entorno
   - con venv: `python -m venv .venv && source .venv/Scripts/activate` (Windows PowerShell: `.venv\\Scripts\\Activate.ps1`)
   - con conda: `conda create -n metaday python=3.10 && conda activate metaday`
2. Instalar Jupyter: `pip install jupyterlab`
3. Abrir el entorno: `jupyter lab`
4. Abrir el notebook del módulo que quieras trabajar.

Nota: Algunos notebooks (p. ej., QLoRA, evaluación o RAG) pueden requerir librerías adicionales como `torch`, `transformers`, `bitsandbytes`, `peft`, `faiss`, `langchain`, `chromadb`, `sentence-transformers`, `unsloth`, etc. Consulta el README de cada módulo para instrucciones específicas.

## Alternativas
- Google Colab: Sube el notebook y usa aceleración de hardware si es necesario. Para Unsloth, usa la versión colab-friendly.
- GPU en la nube: Si vas a ejecutar QLoRA/Unsloth en GPU, usa una instancia con al menos una T4/V100/A100 (BF16 recomendado).

## Licencia y uso
El material se ofrece para fines educativos durante el Meta Day Uruguay 2025. Revisa la licencia del repositorio para condiciones de uso.

## Soporte
Si encuentras un problema, abre un issue en el repositorio o contacta al presentador durante la sesión.

