# 🐳 Módulo 3: Deployment de Ollama

## 🎯 **Objetivo del Módulo**

Aprender a desplegar Llama 3.1 en producción usando Ollama, desarrollar aplicaciones que consuman el modelo via API REST, y crear soluciones escalables para entornos académicos y de investigación en el TEC de Monterrey.

## 📖 **Presentación del Módulo**

**[📊 Módulo 3 - Deployment de Ollama.pdf](./Módulo%203%20-%20Deployment%20de%20Ollama.pdf)**

Esta presentación cubre las estrategias de deployment, arquitecturas de producción y mejores prácticas para implementar Ollama en entornos académicos y de investigación.

---

## 🚀 **¿Qué es Ollama?**

### 🔧 **Características Principales**
- **Deployment simplificado**: Un comando para ejecutar modelos
- **API REST nativa**: Integración fácil con aplicaciones
- **Optimizado para CPU**: Funciona sin GPU (aunque GPU acelera)
- **Gestión de modelos**: Descarga, actualización y versionado automático
- **Multiplataforma**: Windows, macOS, Linux

### 🏫 **Ventajas para Instituciones Académicas**
- **On-premise**: Datos de investigación nunca salen del servidor
- **Escalable**: Múltiples instancias para diferentes proyectos
- **Seguro**: Control total sobre infraestructura del TEC
- **Económico**: Sin costos por token o API calls para investigación

---

## 📁 **Contenido del Módulo**

### 📖 **Presentación**
- **[Módulo 3 - Deployment de Ollama.pdf](./Módulo%203%20-%20Deployment%20de%20Ollama.pdf)**
  - Arquitecturas de deployment
  - Configuración de producción
  - Escalabilidad y alta disponibilidad
  - Monitoreo y mantenimiento

### 📓 **laboratorio-modulo-n3.ipynb**
**Guía completa de instalación, configuración y uso de Ollama**

#### 🛠️ **Secciones Incluidas**
1. **Instalación de herramientas**: VS Code, Python, extensiones
2. **Configuración de entorno**: Virtual environments, dependencias
3. **Instalación de Ollama**: Windows y macOS
4. **Descarga y ejecución**: Modelos Llama 3.1
5. **Consumo via API**: Python requests y ejemplos
6. **Parámetros avanzados**: Temperature, top_p, streaming
7. **Aplicación web**: Mini servidor Flask

---

## 🛠️ **Instalación y Configuración**

### 💻 **Prerrequisitos**

#### 🔧 **Software Base**
- **Visual Studio Code**: Editor recomendado
- **Python 3.10+**: Lenguaje principal
- **Git**: Control de versiones

#### 📦 **Extensiones VS Code**
- **Python** (Microsoft)
- **Jupyter** (Microsoft)

### 🐳 **Instalación de Ollama**

#### 🪟 **Windows**
```bash
# Opción 1: Descarga directa
# Ir a https://ollama.ai/download
# Descargar e instalar el .exe

# Opción 2: Winget (si disponible)
winget install Ollama.Ollama
```

#### 🍎 **macOS**
```bash
# Opción 1: Homebrew
brew install ollama

# Opción 2: Descarga directa
# Ir a https://ollama.ai/download
```

#### 🐧 **Linux**
```bash
curl -fsSL https://ollama.ai/install.sh | sh
```

### ✅ **Verificación**
```bash
ollama --version
# Debería mostrar la versión instalada
```

---

## 🦙 **Gestión de Modelos**

### 📥 **Descargar Llama 3.1**
```bash
# Modelo 8B (recomendado para desarrollo)
ollama pull llama3.1

# Modelo 70B (para producción con GPU potente)
ollama pull llama3.1:70b

# Listar modelos instalados
ollama list
```

### 🚀 **Ejecutar Modelo**
```bash
# Modo interactivo
ollama run llama3.1

# Comando único
ollama run llama3.1 "¿Qué es la inteligencia artificial?"

# Iniciar servidor (automático en instalación)
ollama serve
```

---

## 🌐 **API REST de Ollama**

### 📡 **Endpoint Principal**
```
POST http://localhost:11434/api/generate
```

### 🔧 **Estructura de Request**
```python
import requests

payload = {
    "model": "llama3.1",
    "prompt": "Tu pregunta aquí",
    "stream": False,  # True para streaming
    "options": {
        "temperature": 0.7,
        "top_p": 0.9,
        "top_k": 40
    }
}

response = requests.post(
    "http://localhost:11434/api/generate", 
    json=payload
)
```

### 📊 **Parámetros Importantes**

| Parámetro | Descripción | Rango | Recomendado |
|-----------|-------------|-------|-------------|
| `temperature` | Creatividad | 0.0-2.0 | 0.7 |
| `top_p` | Diversidad | 0.0-1.0 | 0.9 |
| `top_k` | Vocabulario | 1-100 | 40 |
| `repeat_penalty` | Anti-repetición | 1.0-2.0 | 1.1 |

---

## 💻 **Ejemplos de Código**

### 🔤 **Generación Básica**
```python
import requests
import json

OLLAMA_HOST = "http://localhost:11434"

def generar_respuesta(prompt, modelo="llama3.1"):
    payload = {
        "model": modelo,
        "prompt": prompt,
        "stream": False
    }
    
    response = requests.post(f"{OLLAMA_HOST}/api/generate", json=payload)
    return response.json().get("response", "Error")

# Uso
respuesta = generar_respuesta("Explica qué es blockchain")
print(respuesta)
```

### 🌊 **Streaming de Respuestas**
```python
def generar_streaming(prompt, modelo="llama3.1"):
    payload = {
        "model": modelo,
        "prompt": prompt,
        "stream": True
    }
    
    response = requests.post(
        f"{OLLAMA_HOST}/api/generate", 
        json=payload, 
        stream=True
    )
    
    for line in response.iter_lines():
        if line:
            chunk = json.loads(line)
            if not chunk.get("done"):
                print(chunk.get("response", ""), end="", flush=True)
            else:
                print("\n--- Completado ---")
                break

# Uso
generar_streaming("Escribe un poema sobre Argentina")
```

### 🎛️ **Configuración Avanzada**
```python
def generar_con_parametros(prompt, **kwargs):
    config_default = {
        "temperature": 0.7,
        "top_p": 0.9,
        "top_k": 40,
        "repeat_penalty": 1.1,
        "num_predict": 100  # Máximo tokens
    }
    
    # Actualizar con parámetros personalizados
    config_default.update(kwargs)
    
    payload = {
        "model": "llama3.1",
        "prompt": prompt,
        "stream": False,
        "options": config_default
    }
    
    response = requests.post(f"{OLLAMA_HOST}/api/generate", json=payload)
    return response.json().get("response", "Error")

# Uso para diferentes casos
respuesta_creativa = generar_con_parametros(
    "Inventa una historia", 
    temperature=1.2
)

respuesta_tecnica = generar_con_parametros(
    "Explica un algoritmo", 
    temperature=0.3
)
```

---

## 🌐 **Aplicación Web con Flask**

### 🔧 **Servidor Básico**
```python
from flask import Flask, request, jsonify, render_template
import requests

app = Flask(__name__)
OLLAMA_HOST = "http://localhost:11434"

@app.route('/')
def index():
    return render_template('chat.html')

@app.route('/api/chat', methods=['POST'])
def chat():
    data = request.json
    prompt = data.get('prompt', '')
    
    payload = {
        "model": "llama3.1",
        "prompt": prompt,
        "stream": False
    }
    
    try:
        response = requests.post(f"{OLLAMA_HOST}/api/generate", json=payload)
        result = response.json()
        return jsonify({
            "success": True,
            "response": result.get("response", "")
        })
    except Exception as e:
        return jsonify({
            "success": False,
            "error": str(e)
        })

if __name__ == '__main__':
    app.run(debug=True, port=5000)
```

### 🎨 **Frontend HTML**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Chat Gubernamental IA</title>
    <style>
        .chat-container { max-width: 800px; margin: 0 auto; padding: 20px; }
        .message { margin: 10px 0; padding: 10px; border-radius: 5px; }
        .user { background-color: #e3f2fd; text-align: right; }
        .assistant { background-color: #f3e5f5; }
        #input { width: 70%; padding: 10px; }
        #send { padding: 10px 20px; }
    </style>
</head>
<body>
    <div class="chat-container">
        <h1>🏛️ Asistente IA Gubernamental</h1>
        <div id="chat"></div>
        <input type="text" id="input" placeholder="Escribe tu consulta...">
        <button id="send">Enviar</button>
    </div>

    <script>
        // JavaScript para manejar el chat
        document.getElementById('send').onclick = function() {
            const input = document.getElementById('input');
            const message = input.value;
            if (!message) return;
            
            // Mostrar mensaje del usuario
            addMessage(message, 'user');
            input.value = '';
            
            // Enviar a API
            fetch('/api/chat', {
                method: 'POST',
                headers: {'Content-Type': 'application/json'},
                body: JSON.stringify({prompt: message})
            })
            .then(response => response.json())
            .then(data => {
                if (data.success) {
                    addMessage(data.response, 'assistant');
                } else {
                    addMessage('Error: ' + data.error, 'assistant');
                }
            });
        };
        
        function addMessage(text, sender) {
            const chat = document.getElementById('chat');
            const div = document.createElement('div');
            div.className = 'message ' + sender;
            div.textContent = text;
            chat.appendChild(div);
            chat.scrollTop = chat.scrollHeight;
        }
    </script>
</body>
</html>
```

---

## 🏛️ **Casos de Uso Gubernamentales**

### 📋 **1. Centro de Atención Ciudadana**
```python
def asistente_ciudadano(consulta):
    prompt = f"""Eres un asistente del gobierno argentino. 
    Responde de manera oficial y útil a esta consulta ciudadana:
    
    Consulta: {consulta}
    
    Respuesta:"""
    
    return generar_respuesta(prompt)

# Ejemplo
consulta = "¿Cómo renuevo mi pasaporte?"
respuesta = asistente_ciudadano(consulta)
```

### 📄 **2. Análisis de Documentos**
```python
def analizar_documento(texto_documento):
    prompt = f"""Analiza este documento oficial y proporciona:
    1. Resumen ejecutivo
    2. Puntos clave
    3. Acciones requeridas
    
    Documento:
    {texto_documento}
    
    Análisis:"""
    
    return generar_respuesta(prompt, num_predict=300)
```

### 🌐 **3. Traducción Académica**
```python
def traducir_paper(texto, idioma_destino="inglés"):
    prompt = f"""Traduce este abstract de investigación al {idioma_destino},
    manteniendo el tono académico y la precisión técnica:

    {texto}

    Traducción:"""

    return generar_respuesta(prompt)
```

---

## 🔧 **Monitoreo y Mantenimiento**

### 📊 **Métricas de Rendimiento**
```python
import time
import psutil

def monitorear_ollama():
    start_time = time.time()
    
    # Test de respuesta
    respuesta = generar_respuesta("Test de conectividad")
    
    response_time = time.time() - start_time
    cpu_usage = psutil.cpu_percent()
    memory_usage = psutil.virtual_memory().percent
    
    return {
        "response_time": response_time,
        "cpu_usage": cpu_usage,
        "memory_usage": memory_usage,
        "status": "OK" if respuesta else "ERROR"
    }
```

### 🔄 **Gestión de Modelos**
```bash
# Actualizar modelo
ollama pull llama3.1

# Eliminar modelo no usado
ollama rm old-model

# Ver uso de espacio
ollama list
```

---

## ⏱️ **Tiempo Estimado**

- **Presentación PDF**: 30 minutos
- **Instalación y configuración**: 45 minutos
- **Primeras pruebas con API**: 30 minutos
- **Desarrollo de aplicación**: 75 minutos
- **Casos de uso gubernamentales**: 45 minutos
- **Total**: **3-4 horas**

---

## 🔧 **Solución de Problemas**

### ❌ **Errores Comunes**

#### 🔌 **Ollama no responde**
```bash
# Verificar si está corriendo
ollama list

# Reiniciar servicio
ollama serve
```

#### 💾 **Modelo no encontrado**
```bash
# Verificar modelos instalados
ollama list

# Descargar si falta
ollama pull llama3.1
```

#### 🌐 **Error de conexión**
```python
# Verificar conectividad
import requests
try:
    response = requests.get("http://localhost:11434/api/tags")
    print("Ollama conectado:", response.status_code == 200)
except:
    print("Ollama no disponible")
```

---

## ➡️ **Siguiente Paso**

Una vez completado este módulo, continúa con:
**[Módulo 4: Optimización y Fine-tuning](../módulo%204/README.md)**

---

**¡Despliega Llama 3.1 en producción para proyectos académicos del TEC! 🏫🐳**
