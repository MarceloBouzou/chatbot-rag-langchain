# Caso de Estudio: Chatbot RAG con Python y LangChain

## (Resumen del Proyecto)

Este repositorio documenta un proyecto de investigación y desarrollo personal para construir e implementar un **Chatbot con arquitectura RAG (Retrieval-Augmented Generation)**. El objetivo fue explorar cómo aplicar los Large Language Models (LLMs) a un contexto de negocio específico, asegurando que las respuestas sean precisas y se basen únicamente en una fuente de conocimiento controlada.

El proyecto abarcó el ciclo de vida completo: desde el diseño del backend en **Python** con **LangChain**, hasta el despliegue como una aplicación web en **Render.com** y su integración en un sitio real.

**Puede ver el chatbot en acción en el pie de página de [este sitio web](https://sites.google.com/view/macetascharo/).** (Nota: al ser un plan gratuito de Render.com, el chatbot puede tardar unos segundos en "despertar" en el primer uso).

---

## 🎯 El Desafío: Superar las Limitaciones de los LLMs Genéricos

Los LLMs como los modelos de OpenAI o Gemini son increíblemente potentes, pero para un negocio presentan dos grandes desafíos:

1.  **Falta de Conocimiento Específico:** No conocen los productos, horarios, políticas o detalles de un negocio en particular.
2.  **Riesgo de "Alucinaciones":** Pueden inventar respuestas que suenan convincentes pero son incorrectas, lo que es inaceptable para la comunicación con un cliente.

El desafío era crear un asistente de IA que fuera **fiable, preciso y un verdadero experto** en la información de un único comercio, utilizando su propio documento de texto (`.txt`) como única fuente de verdad.

---

## 🛠️ Mi Solución: Una Arquitectura RAG End-to-End

Diseñé e implementé una solución completa que no solo responde preguntas, sino que lo hace de una manera controlada y verificable.

### Arquitectura y Flujo de Trabajo:

1.  **Base de Conocimiento:** Se utilizó un archivo de texto (`knowledge_base.txt`) que contiene toda la información relevante del comercio (productos, precios, horarios, métodos de envío, etc.).
2.  **Backend con Python y LangChain:**
    *   **Carga y División:** El script carga el `.txt` y lo divide en fragmentos de texto manejables (chunks).
    *   **Vectorización (Embeddings):** Utilizando los modelos de embeddings de OpenAI, cada fragmento de texto se convierte en un vector numérico que representa su significado semántico.
    *   **Almacenamiento Vectorial:** Estos vectores se almacenan en una base de datos vectorial en memoria (FAISS), que permite búsquedas de similitud increíblemente rápidas.
3.  **Lógica de Respuesta RAG:**
    *   Cuando un usuario hace una pregunta, esta también se convierte en un vector.
    *   El sistema realiza una **búsqueda semántica** en la base de datos vectorial para encontrar los fragmentos de texto más relevantes para la pregunta.
    *   Estos fragmentos relevantes se inyectan en el "prompt" que se envía al LLM de OpenAI, junto con la pregunta original y una instrucción clara: **"Responde a esta pregunta basándote ÚNICAMENTE en el siguiente contexto"**.
4.  **Despliegue como API Web:**
    *   Utilicé **Flask** para envolver la lógica del chatbot en una API web simple con un endpoint `/ask`.
    *   Desplegué la aplicación en **Render.com**, configurando el entorno para instalar todas las dependencias de Python y ejecutar el servidor Flask.
5.  **Integración Frontend:** El chatbot fue integrado en el sitio de Google Sites mediante un simple `<iframe>` y código JavaScript que realiza las llamadas a la API desplegada en Render.

---

## 🚀 Impacto y Capacidades Demostradas

Aunque fue un proyecto de aprendizaje, demostró mi capacidad para ejecutar iniciativas de IA de alto valor:

*   **Dominio de Arquitecturas de IA Modernas:** Demostré la capacidad de construir y entender sistemas RAG, la arquitectura estándar de la industria para aplicaciones de LLMs basadas en conocimiento.
*   **Ciclo de Vida de Desarrollo End-to-End:** Probé mi habilidad para llevar un concepto desde un script de Python local hasta una **aplicación web funcional y desplegada en la nube**, accesible para usuarios reales.
*   **Capacidad de Prototipado Rápido:** Fui capaz de pasar de una idea a un prototipo funcional en un corto período de tiempo, demostrando agilidad y una rápida curva de aprendizaje.
*   **Aplicación Práctica de la IA al Negocio:** Demostré cómo la IA puede ser utilizada de forma segura y eficaz para resolver un problema de negocio real: proporcionar atención al cliente 24/7 con información precisa y verificada.

---

## 💻 Stack Tecnológico

*   **Lenguaje:** Python
*   **Frameworks de IA:** LangChain
*   **Modelos:** OpenAI (Embeddings y LLM)
*   **Base de Datos Vectorial:** FAISS
*   **Framework Web/API:** Flask
*   **Plataforma de Despliegue (PaaS):** Render.com
*   **Frontend:** Google Sites, HTML, JavaScript
