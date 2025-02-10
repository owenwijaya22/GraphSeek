# 📈 **GraphSeek – Your Personal Document AI on steroids!**

**(100% Free, Private (No Internet), and Local PC Installation)**  

## **💡 What sets GraphSeek apart from others**

- 🕸️ **GraphRAG Integration**: Enhances retrieval by constructing a **Knowledge Graph** from your documents, allowing for more contextual and relational understanding
- 🔍 **Neural Reranking**: Fine-tuned result ranking using cross-encoders
- 🎯 **HyDE Technology**: Hypothetical Document Embeddings for better retrieval
- 🌟 **NOMIC Embeddings**: Advanced semantic understanding of your documents
- 📊 **FAISS Vector Search**: Lightning-fast similarity search engine
- 📘 **BM25**: Classic keyword-based search for exact matches
- 🧠 **DeepSeek-7B LLM**: State-of-the-art language model for precise responses
- 💬 **Intelligent Chat Memory**: Contextual awareness across conversations that makes a coherent user experience
- 🛠️ **Improved Error Handling**: Resolved issues related to chat history clearing and other minor bugs for a smoother user experience

## **🚀 Quick Start**

### **1️⃣ Clone the Repository Code & Install Dependencies**

  ```bash
  git clone https://github.com/owenwijaya22/GraphSeek.git
  cd GraphSeek
  python -m venv venv
  venv/Scripts/activate
  pip install -r requirements.txt
  ```

### **2️⃣ Download & Set Up Ollama**

Ollama is required to run **DeepSeek-7B** and **Nomic Embeddings** locally.  
🔗 **Download Ollama** → [https://ollama.com/](https://ollama.com/)  

Then, get the required models:
  ```bash
  ollama pull deepseek-r1:7b
  ollama pull nomic-embed-text
  ```

### **3️⃣ Run the Application**
1. Make sure **Ollama** is running on your system:
   ```
   ollama serve
   ```
2. Launch the Streamlit app:
   ```bash
   streamlit run app.py
   ```
## **2️⃣ Docker Installation**

### **A) Single-Container Approach (Ollama on Your Host)**

If **Ollama** is already **installed on your host machine** and listening at `localhost:11434`, do the following:

1. **Build & Run**:
   ```
   docker-compose build
   docker-compose up
   ```
2. The app is now served at **[http://localhost:8501](http://localhost:8501)**. Ollama runs on your host, and the container accesses it via the specified URL.

### **B) Two-Container Approach (Ollama in Docker)**

If you prefer **everything** in Docker:
```
version: "3.8"

services:
  ollama:
    image: ghcr.io/jmorganca/ollama:latest
    container_name: ollama
    ports:
      - "11434:11434"

  graphseek-service:
    container_name: graphseek-service
    build: .
    ports:
      - "8501:8501"
    environment:
      - OLLAMA_API_URL=http://ollama:11434
      - MODEL=deepseek-r1:7b
      - EMBEDDINGS_MODEL=nomic-embed-text:latest
      - CROSS_ENCODER_MODEL=cross-encoder/ms-marco-MiniLM-L-6-v2
    depends_on:
      - ollama
```

Then:
```
docker-compose build
docker-compose up
```
Both **Ollama** and the chatbot run in Docker. Access the chatbot at **[http://localhost:8501](http://localhost:8501)**.

## **📌 How It Works**
1. 📥 **Document Processing**
- Upload your PDFs, DOCX, or TXT files
- Smart parsing and chunking
- Automatic metadata extraction
2. 🔄 **Advanced Retrieval Pipeline**
- Hybrid Search System:
  - BM25 for keyword precision
  - FAISS for semantic matching
  - Real-time result fusion
3. 📊 **Knowledge Graph Construction**
- Dynamic graph building
  - Entity relationship mapping
  - Context enrichment
  - Semantic network creation
4. 🎯 **Precision Enhancement**
- Multi-Stage Refinement:
  - Cross-encoder reranking
  - Relevance scoring
  - Context-aware filtering
5. 🧬 **Query Intelligence**
- HyDE Technology:
  - Query expansion
  - Hypothetical embedding
  - Enhanced recall
6. 💭 **Conversational Memory**
- References previous interactions
- Context preservation, retrieval, and tracking
7. 🧠 **Response Generation**
- DeepSeek-7B processing
- Context-aware synthesis
- Natural language output

---

## **🔹 What's New in This Release?**
| Feature | Previous Version | New Version |
|---------|------------------|-------------|
| **Retrieval Method** | Hybrid (BM25 + FAISS) | Hybrid + **Knowledge Graph** |
| **Contextual Depth** | Surface-Level | **Deep Graph-Based Understanding** |
| **Interface Design** | Light Theme Only | **Dark Theme with Customizable Sidebar** |
| **Memory System** | Stateless | **Smart Conversation Memory** |
| **Reliability** | Base Level | **Enhanced Stability + Fixes** |

---

## **📌 Common Issues & Fixes**
💡 **Issue:** Error when clearing chat history.  
✅ **Fix:** Ensure you're using the latest version of Streamlit, as `st.experimental_rerun()` has been updated.  
```bash
pip install --upgrade streamlit
```

---

## **📌 Contributing**
🚀 Want to improve this chatbot? Feel free to **fork this repo**, submit **pull requests**, or **report issues**!  

---

### **🔗 Connect & Share Your Thoughts!**
Got feedback or suggestions? Let’s discuss on **[Linkedin]([https://www.linkedin.com/in/owen-valentinus/)**! 🚀💡 
