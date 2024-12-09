### **Aplicación Data Driven con ejemplos** 

Este README proporciona una guía detallada para construir y actualizar una aplicación RAG siguiendo dos tutoriales oficiales de LangChain. Utilizaremos **Python 3.11.6** y un entorno virtual para garantizar la organización y aislamiento del entorno de desarrollo siguiendo la siguiente arquitectura.

![image](https://github.com/user-attachments/assets/d88df605-6259-4b21-ba6a-47c8ea9aa1b5)
  

---

## **Requisitos previos**  

### Software necesario  
1. **Python 3.11.6**: [Descargar aquí](https://www.python.org/downloads/).  
2. Un editor de código, como [VS Code](https://code.visualstudio.com/).

### Servicios necesarios  
1. **Clave API de OpenAI**: Regístrate en [OpenAI](https://platform.openai.com/) para obtener acceso.  
2. **Cuenta en Pinecone**: Regístrate en [Pinecone](https://www.pinecone.io/) para almacenar y recuperar embeddings.  

---

## **Parte 1: Construcción de una Aplicación RAG Básica**  

### Paso 1: Configurar el entorno de desarrollo  

1. Abre una terminal y navega al directorio donde deseas trabajar.  
2. Crea un entorno virtual ejecutando:  
   ```bash
   python3.11 -m venv env
   ```  
3. Activa el entorno virtual:  
   - **Windows**:  
     ```bash
     .\env\Scripts\activate
     ```  
   - **Mac/Linux**:  
     ```bash
     source env/bin/activate
     ```  

### Paso 2: Instalar las dependencias básicas  

Ejecuta el siguiente comando para instalar los paquetes necesarios para trabajar con LangChain y OpenAI:  
```bash
pip install langchain openai
```  

### Paso 3: Construir la aplicación RAG  

Sigue el tutorial detallado en **[Build a Retrieval Augmented Generation (RAG) App: Part 1](https://python.langchain.com/docs/tutorials/rag/)**.  
En este tutorial:  
1. Configurarás tu clave API de OpenAI para interactuar con el modelo GPT.  
2. Crearás un flujo básico de recuperación y generación:  
   - Configura un conjunto de datos que servirá como fuente de conocimiento.  
   - Implementa una clase para manejar consultas y respuestas contextuales.  
3. Ejecuta el ejemplo para generar respuestas utilizando el contexto recuperado.  

### Código base proporcionado en el tutorial:  
Sigue paso a paso las secciones del tutorial para entender cómo cargar documentos, implementar el **Retriever** y utilizar LangChain para la generación de respuestas.  

---

## **Parte 2: Actualizar la App RAG para Usar Pinecone**  

### Paso 1: Instalar dependencias adicionales  

Para integrar Pinecone como vector store, instala el cliente de Pinecone:  
```bash
pip install pinecone-client
```  

### Paso 2: Configurar Pinecone  

1. Inicia sesión en [Pinecone](https://www.pinecone.io/) y genera una clave API desde tu panel de control.  
2. Configura un índice en Pinecone siguiendo las instrucciones del tutorial. Esto incluye:  
   - Seleccionar dimensiones adecuadas para tus embeddings.  
   - Configurar políticas de replicación y métricas.  

### Paso 3: Integrar Pinecone con LangChain  

Sigue el tutorial detallado en **[Update the RAG to store and retrieve vector embeddings from Pinecone](https://python.langchain.com/docs/integrations/vectorstores/pinecone/)**.  
En este tutorial:  
1. Aprenderás a inicializar una conexión con Pinecone utilizando la clave API.  
2. Configurarás el almacenamiento de embeddings generados por OpenAI.  
3. Actualizarás la lógica de recuperación para consultar Pinecone y generar respuestas más relevantes.  

### Ejemplo de flujo del tutorial:  
1. **Carga de datos**: Carga documentos desde tu fuente de conocimiento.  
2. **Vectorización**: Usa un modelo como `text-embedding-3-large` de OpenAI para generar embeddings.  
3. **Almacenamiento en Pinecone**: Guarda los embeddings en el índice configurado.

   - Si la carga quedo correctamente en Pinecone se deberian ver de la siguiente forma

   ![image](https://github.com/user-attachments/assets/2e4b3a78-e09b-4ff0-b28a-c0169482196e)
   ![image](https://github.com/user-attachments/assets/c081717f-7c49-4764-a21d-094ed9341ece)
   ![image](https://github.com/user-attachments/assets/b51cde29-6ccf-4f7a-8b1f-4c1f41e8538d)
   ![image](https://github.com/user-attachments/assets/40d19c77-a1c9-4e5c-a86b-3849f32eeee8)

4. **Generación de Respuestas**: Combina los datos recuperados con LangChain para construir una respuesta final.  

---

## **Ejecución de la Aplicación**  

### Paso 1: Correr el código  
1. Asegúrate de activar tu entorno virtual:  
   - **Windows**:  
     ```bash
     .\env\Scripts\activate
     ```  
   - **Mac/Linux**:  
     ```bash
     source env/bin/activate
     ```  
2. Ejecuta el archivo principal de tu proyecto:  
   ```bash
   python main.py
   ```  

### Paso 2: Verifica la interacción  
Prueba enviando consultas al modelo y observa cómo se generan las respuestas utilizando los datos recuperados desde Pinecone.  

---

## **Notas importantes**  

1. **Gestión de claves API**:  
   - Usa un archivo `.env` para almacenar claves sensibles. Ejemplo:  
     ```env
     OPENAI_API_KEY=tu_clave_openai
     PINECONE_API_KEY=tu_clave_pinecone
     PINECONE_ENVIRONMENT=tu_entorno_pinecone
     ```  
   - Instala el paquete `python-dotenv` para cargar variables de entorno:  
     ```bash
     pip install python-dotenv
     ```  

2. **Entorno Jupyter (Opcional)**:  
   Si deseas usar Jupyter Notebook para experimentar, instala el kernel e intégralo es muy importante la versión de python ya que en superiores ya no es posible usar las librerías del tutorial:  
   ```bash
   pip install ipykernel
   python -m ipykernel install --user --name=env --display-name "Python 3.11.6 (env)"
   ```  

---

## **Referencias**  
- [LangChain Documentation](https://python.langchain.com/)  
- [Pinecone Documentation](https://docs.pinecone.io/)  

Este README garantiza que tengas un flujo claro y profesional para implementar y actualizar tu aplicación RAG utilizando LangChain y Pinecone.
