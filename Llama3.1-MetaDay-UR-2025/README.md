# Llama 3.1 – Meta Day Uruguay (19 de agosto de 2025)

Este directorio contiene el material de apoyo para la charla/taller de Meta Day en Uruguay sobre Llama 3.1.

## Estructura
- módulo 1: Fundamentos y atención (demo + laboratorio)
- módulo 2: Laboratorio módulo 2
- módulo 3: Laboratorio módulo 3
- módulo 4: Fine-tuning con QLoRA (CPU/GPU)
- módulo 5: RAG con Ollama

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

Nota: Algunos notebooks (p. ej., QLoRA o RAG) pueden requerir librerías adicionales como `torch`, `transformers`, `bitsandbytes`, `peft`, `faiss`, `langchain`, `ollama`, etc. Consulta el README de cada módulo para instrucciones específicas.

## Alternativas
- Google Colab: Sube el notebook y usa aceleración de hardware si es necesario.
- GPU en la nube: Si vas a ejecutar QLoRA en GPU, usa una instancia con al menos una A100/T4/V100.

## Licencia y uso
El material se ofrece para fines educativos durante el Meta Day Uruguay 2025. Revisa la licencia del repositorio para condiciones de uso.

## Soporte
Si encuentras un problema, abre un issue en el repositorio o contacta al presentador durante la sesión.

