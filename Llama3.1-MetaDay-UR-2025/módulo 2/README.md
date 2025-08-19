# Módulo 2 – Laboratorio Módulo 2

## Contenido
- laboratorio-modulo-n2.ipynb: Ejercicios prácticos del módulo 2.
- 📑 Diapositivas: “Módulo 2 - Configuración de Entorno.pdf”

## Objetivos
- Profundizar en conceptos intermedios de Llama 3.1
- Aplicar técnicas de procesamiento de texto y embeddings
- Introducir prácticas de evaluación ligera de outputs

## Requisitos
- Python 3.10+
- Jupyter Lab/Notebook
- torch, transformers (instalar con: `pip install torch transformers`)

## Ejecución rápida
1. Instalar dependencias: `pip install torch transformers numpy matplotlib`
2. Abre Jupyter Lab: `jupyter lab`
3. Navega a este directorio y abre laboratorio-modulo-n2.ipynb
4. Ejecuta las celdas en orden

## Dependencias adicionales
Si el notebook requiere librerías específicas, instálalas según aparezcan en las primeras celdas:
```bash
pip install sentence-transformers
pip install datasets accelerate
# Opcional para evaluación ligera
pip install evaluate rouge-score
```

## Notas
- Algunos ejercicios pueden requerir descarga de modelos pre-entrenados
- Tiempo estimado de ejecución: 15-30 minutos dependiendo del hardware
