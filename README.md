[index (2).html](https://github.com/user-attachments/files/25536762/index.2.html)# 👔 AI Agent Chat

Interfaz web de chat conectada a un agente de inteligencia artificial construido en **n8n Cloud**, con memoria de conversación y acceso desde cualquier dispositivo con navegador. Completamente gratuito y sin límite de tiempo.

---

## 🌐 Enlace del chat

👉 (https://github.com/user-attachments/files/25536762/index.2.html)


---

## ✨ Características

- 💬 Chat en tiempo real con el agente de IA
- 🧠 Memoria de conversación — el agente recuerda el contexto de la sesión
- 📱 Diseño responsive — funciona en celular, tablet y escritorio
- ⚡ Sin instalación — se abre directo en el navegador
- 🆓 100% gratuito — sin costos de modelo ni de hosting
- 🔒 Sin almacenamiento de datos personales

---

## 🛠️ Tecnologías utilizadas

| Tecnología | Uso | Costo |
|---|---|---|
| **n8n Cloud** | Motor del agente y automatización | Gratuito |
| **Groq API** | Modelo de lenguaje (LLM) — Llama 3.3 70B | Gratuito |
| **HTML / CSS / JS** | Interfaz web (sin frameworks) | — |
| **GitHub Pages** | Hosting permanente del chat | Gratuito |
| **GitHub** | Repositorio y control de versiones | Gratuito |

---

## 🏗️ Arquitectura

```
Usuario escribe mensaje
        ↓
  Interfaz Web (index.html)
  GitHub Pages — enlace permanente
        ↓
  Webhook POST → n8n Cloud
        ↓
  AI Agent + Simple Memory (sesión)
        ↓
  Groq API — Llama 3.3 70B (gratis)
        ↓
  Respuesta → de vuelta al chat
```

---

## 🚀 Cómo usar

1. Abre el enlace del chat
2. Escribe tu mensaje y presiona **Enter**
3. El agente responderá en segundos

No necesitas crear cuenta ni instalar nada.

---

## ⚙️ Configuración técnica

### Requisitos
- Cuenta en [n8n Cloud](https://app.n8n.cloud) — gratuita
- Cuenta en [Groq](https://console.groq.com) — gratuita, sin tarjeta
- Cuenta en [GitHub](https://github.com) — gratuita

### Variable configurada en `index.html`

```javascript
const N8N_WEBHOOK_URL = 'https://yotrif.app.n8n.cloud/webhook/cc7ba324-b263-42fa-ab09-b10e412d96d6';
```

### Estructura del proyecto

```
ai-agent-chat/
├── index.html    ← Interfaz web completa
└── README.md     ← Este archivo
```

---

## 📋 Workflow de n8n

```
Webhook (POST) → AI Agent → Respond to Webhook
                    ↑
             Groq Chat Model
             (Llama 3.3 70B)
             Simple Memory
```

### Nodo Webhook
| Campo | Valor |
|---|---|
| **Method** | POST |
| **CORS** | `*` |
| **Respond** | Using Respond to Webhook Node |

### Nodo AI Agent
| Campo | Valor |
|---|---|
| **Source** | Define below |
| **Prompt** | `{{ $json.body.message }}` |

### Nodo Simple Memory
| Campo | Valor |
|---|---|
| **Session ID** | `{{ $json.body.sessionId }}` |

### Nodo Groq Chat Model
| Campo | Valor |
|---|---|
| **Model** | `openai/gpt-3.5-turbo-instruct` |
| **Credential** | Groq API Key |

### Nodo Respond to Webhook
| Campo | Valor |
|---|---|
| **Respond With** | First Entry JSON |

---

## 🔄 Cómo actualizar el chat

1. Edita `index.html` en tu computadora
2. Ve al repositorio en GitHub
3. Abre el archivo → click en ✏️ (lápiz)
4. Pega el nuevo contenido
5. Click en **"Commit changes"**

Los cambios se publican automáticamente en 1-2 minutos.

---

## 📊 Límites de Groq (plan gratuito)

| Modelo | Requests/minuto | Tokens/minuto | Tokens/día |
|---|---|---|---|
| Llama 3.3 70B | 30 | 6,000 | 500,000 |

Con 500,000 tokens diarios gratuitos tienes para cientos de conversaciones por día sin costo.

---

## 📄 Licencia

Uso educativo.

---

Desarrollado por SAMUEL usando n8n + Groq + Claude AI
