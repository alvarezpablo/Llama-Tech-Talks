# 🦙 Módulo 2: Introducción a Llama 3.1

## 🎯 **Objetivo del Módulo**

Dominar el uso práctico de Llama 3.1, desde la carga optimizada del modelo hasta la implementación de casos de uso específicos para aplicaciones gubernamentales.

---

## 🚀 **Características de Llama 3.1**

### ⚡ **Especificaciones Técnicas**
- **Parámetros**: 8B, 70B, 405B
- **Contexto**: Hasta 128K tokens
- **Idiomas**: Multilingüe (incluye español)
- **Capacidades**: Texto, código, razonamiento, matemáticas

### 🏛️ **Ventajas para Gobierno**
- **On-premise**: Control total de datos
- **Personalizable**: Fine-tuning específico
- **Eficiente**: Optimizaciones avanzadas
- **Seguro**: Sin envío de datos externos

---

## 📁 **Contenido del Módulo**

### 📓 **laboratorio-modulo-n2.ipynb**
**Notebook principal con demostración completa de Llama 3.1**

#### 🔧 **Configuración Automática**
- **Detección de entorno**: Kaggle, Colab, Local
- **Gestión de tokens**: Variables de ambiente automáticas
- **Optimización de memoria**: Cuantización 4-bit
- **Configuración GPU**: Detección y uso automático

#### 🦙 **Clase Llama31Demo**
```python
class Llama31Demo:
    def cargar_modelo_cuantizado(self)     # Carga optimizada
    def cargar_modelo_basico(self)         # Carga estándar
    def demo_capacidades_basicas(self)     # Generación general
    def demo_capacidades_conversacionales(self)  # Chat
    def demo_capacidades_multilingues(self)      # Idiomas
    def demo_generacion_codigo(self)       # Programación
    def analizar_rendimiento(self)         # Métricas
```

---

## 🛠️ **Configuración y Requisitos**

### 💻 **Hardware Recomendado**
- **RAM**: 16GB mínimo (32GB recomendado)
- **GPU**: NVIDIA con 8GB+ VRAM
- **Almacenamiento**: 20GB libres para modelo

### 🐍 **Dependencias**
```bash
pip install transformers torch accelerate bitsandbytes
pip install matplotlib seaborn psutil
```

### 🔑 **Token Hugging Face**
```bash
# Opción 1: Variable de ambiente (recomendado)
export HF_TOKEN="hf_tu_token_aqui"

# Opción 2: Kaggle Secrets
# Settings > Secrets > Add Secret: HF_TOKEN

# Opción 3: Google Colab
# os.environ['HF_TOKEN'] = 'tu_token'
```

---

## 🚀 **Inicio Rápido**

### 1️⃣ **Configuración Inicial**
```python
# El notebook detecta automáticamente el entorno
entorno = detectar_entorno()  # Kaggle/Colab/Local
print(f"🔍 Entorno detectado: {entorno}")

# Configuración automática de autenticación
auth_success = setup_huggingface_auth()
```

### 2️⃣ **Carga del Modelo**
```python
# Crear instancia
demo = Llama31Demo()

# Cargar con cuantización (recomendado)
exito = demo.cargar_modelo_cuantizado()

# Fallback a modelo básico si es necesario
if not exito:
    demo.cargar_modelo_basico()
```

### 3️⃣ **Primeras Pruebas**
```python
# Capacidades básicas
demo.demo_capacidades_basicas()

# Conversación
demo.demo_capacidades_conversacionales()

# Multilingüe
demo.demo_capacidades_multilingues()
```

---

## 🎯 **Demostraciones Incluidas**

### 🔤 **1. Capacidades Básicas**
- **Explicaciones**: Conceptos técnicos simplificados
- **Generación de código**: Python, JavaScript, SQL
- **Análisis**: Beneficios de tecnologías
- **Traducción**: Múltiples idiomas
- **Matemáticas**: Resolución de problemas

### 💬 **2. Capacidades Conversacionales**
- **Sistema de chat**: Formato de conversación
- **Contexto persistente**: Memoria de conversación
- **Roles definidos**: System, User, Assistant
- **Personalización**: Ajuste de personalidad

### 🌍 **3. Capacidades Multilingües**
- **Español**: Idioma nativo optimizado
- **Inglés**: Rendimiento superior
- **Francés, Alemán, Italiano**: Soporte robusto
- **Portugués**: Excelente para región

### 💻 **4. Generación de Código**
- **Python**: Scripts y funciones
- **JavaScript**: Aplicaciones web
- **SQL**: Consultas de base de datos
- **Bash**: Scripts de automatización

---

## ⚙️ **Optimizaciones Implementadas**

### 🔧 **Cuantización 4-bit**
```python
bnb_config = BitsAndBytesConfig(
    load_in_4bit=True,
    bnb_4bit_use_double_quant=True,
    bnb_4bit_quant_type="nf4",
    bnb_4bit_compute_dtype=torch.bfloat16,
)
```

**Beneficios:**
- ✅ **60% menos memoria**
- ✅ **Velocidad similar**
- ✅ **Calidad preservada**

### 🚀 **Configuración Automática**
- **Device mapping**: Distribución automática en GPU
- **Memory management**: Gestión eficiente de memoria
- **Fallback models**: Modelos alternativos si falla
- **Error handling**: Manejo robusto de errores

---

## 🏛️ **Casos de Uso Gubernamentales**

### 📋 **1. Atención Ciudadana**
```python
conversacion = [
    {"role": "system", "content": "Eres un asistente del gobierno argentino..."},
    {"role": "user", "content": "¿Cómo tramito mi DNI?"}
]
respuesta = demo._generar_respuesta_chat(conversacion)
```

### 📄 **2. Análisis de Documentos**
```python
prompt = "Resume este documento oficial: [TEXTO_DOCUMENTO]"
resumen = demo._generar_respuesta(prompt, max_tokens=200)
```

### 🌐 **3. Traducción Oficial**
```python
prompt = "Traduce al inglés este comunicado oficial: [TEXTO]"
traduccion = demo._generar_respuesta(prompt)
```

### 💻 **4. Automatización**
```python
prompt = "Genera un script Python para procesar formularios ciudadanos"
codigo = demo._generar_respuesta(prompt, max_tokens=300)
```

---

## 📊 **Análisis de Rendimiento**

### 🔍 **Métricas Incluidas**
- **Tiempo de carga**: Segundos para cargar modelo
- **Uso de memoria**: RAM y VRAM utilizadas
- **Velocidad de generación**: Tokens por segundo
- **Calidad de respuesta**: Evaluación cualitativa

### 📈 **Benchmarks Típicos**
- **Carga cuantizada**: ~3 minutos
- **Memoria utilizada**: ~6GB VRAM
- **Generación**: ~20 tokens/segundo
- **Contexto máximo**: 128K tokens

---

## 🎓 **Ejercicios Prácticos**

### 🔧 **Ejercicio 1: Configuración Personalizada**
```python
# Modificar parámetros de generación
config_personalizada = {
    "temperature": 0.3,  # Más determinista
    "top_p": 0.8,       # Menos diversidad
    "max_tokens": 150   # Respuestas más cortas
}
```

### 💬 **Ejercicio 2: Chat Gubernamental**
```python
# Crear un asistente especializado
sistema = """Eres un asistente del Ministerio de Modernización.
Ayudas con trámites digitales y servicios online."""

# Implementar conversación multi-turno
```

### 🌍 **Ejercicio 3: Traducción Oficial**
```python
# Traducir comunicados oficiales
documentos = [
    "Decreto presidencial sobre digitalización",
    "Resolución ministerial de transparencia",
    "Comunicado de prensa gubernamental"
]
```

---

## 🔧 **Solución de Problemas**

### ❌ **Errores Comunes**

#### 🔑 **Token no configurado**
```
Error: Repository not found or access denied
Solución: Configurar HF_TOKEN correctamente
```

#### 💾 **Memoria insuficiente**
```
Error: CUDA out of memory
Solución: Usar cuantización o modelo más pequeño
```

#### 🌐 **Conexión fallida**
```
Error: Connection timeout
Solución: Verificar conexión a internet
```

---

## ⏱️ **Tiempo Estimado**

- **Configuración inicial**: 30 minutos
- **Carga de modelo**: 15 minutos
- **Demostraciones**: 120 minutos
- **Ejercicios prácticos**: 60 minutos
- **Total**: **3-4 horas**

---

## 📚 **Recursos Adicionales**

### 🔗 **Enlaces Útiles**
- [Llama 3.1 Model Card](https://huggingface.co/meta-llama/Meta-Llama-3.1-8B-Instruct)
- [Transformers Documentation](https://huggingface.co/docs/transformers/)
- [BitsAndBytes Guide](https://huggingface.co/docs/bitsandbytes/)

### 📖 **Documentación Técnica**
- [Llama 3.1 Paper](https://ai.meta.com/research/publications/the-llama-3-herd-of-models/)
- [Quantization Techniques](https://arxiv.org/abs/2208.07339)

---

## ➡️ **Siguiente Paso**

Una vez completado este módulo, continúa con:
**[Módulo 3: Deployment con Ollama](../módulo%203/README.md)**

---

**¡Domina Llama 3.1 para revolucionar los servicios gubernamentales! 🏛️🦙**
