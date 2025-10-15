
**README.md**

---

# 🚀 **Model Training From Documents v1**  
*Automate AI data preparation for model training and RAG systems using n8n*

---

## 📌 Overview  
This workflow is part of Koa Research Group's open-source toolkit, designed to streamline the process of transforming raw documents (PDFs, Google Docs, etc.) into structured, machine-readable data suitable for **AI model training** or **retrieval-augmented generation (RAG)** systems. It leverages **n8n**, **Google Drive**, **Postgres**, and **Ollama** to automate tasks like text extraction, chunking, embedding, and metadata storage.

---

## 🛠️ Prerequisites  
Before running this workflow, ensure you have the following installed/configured:  

1. **n8n** (open-source workflow automation tool)  
   - [Install n8n](https://docs.n8n.io/)  
2. **Google Drive API access** for document ingestion  
3. **PostgreSQL with PGVector extension** for embedding storage  
4. **Ollama** or compatible LLM for generating embeddings (e.g., Llama 3)  
5. Access to Koa Research Group's GitHub repositories:  
   - [Docling](https://github.com/KoaResearchGroup/docling) – Document extraction library  
   - [Notebooks](https://github.com/KoaResearchGroup/notebooks) – Fine-tuning scripts  

---

## 📁 File Structure  
```
project-root/
├── workflows/                # Contains this workflow
│   └── model-training-v1.n8n  # Main workflow file
└── README.md                 # This file
```

---

## 🔧 Setup Instructions  

### 1. Clone the Repository  
```bash
git clone https://github.com/KoaResearchGroup/n8n.git
cd n8n
```

### 2. Configure Environment Variables  
Set up required environment variables for Google Drive, Postgres, and Ollama:  

```env
GOOGLE_DRIVE_CLIENT_ID=your-client-id
GOOGLE_DRIVE_CLIENT_SECRET=your-secret
POSTGRES_URL=postgres://user:password@localhost:5432/dbname
OLLAMA_HOST=http://localhost:11434

```

---

## 🔄 Workflow Overview  
This workflow processes documents in the following steps:  

1. **Trigger** (Google Drive File Created) → Start processing new files  
2. **Loop Over Items** → Handle batch uploads (PDFs, Google Docs)  
3. **Delete Old Data** → Avoid duplicates by purging previous entries  
4. **Text Extraction** → Use Docling-inspired methods to extract text  
5. **Chunking** → Split text into manageable pieces for embedding  
6. **Embedding Generation** → Generate vector embeddings using Ollama  
7. **Metadata Storage** → Save file details in Postgres (with PGVector)  
8. **Training Data Output** → Export structured data for fine-tuning  

---

## 🧪 Usage Instructions  

### 1. Upload Documents to Google Drive  
Place your files in a designated folder, e.g., `koaresearch-group-documents`. The workflow will trigger automatically when new files are added.

### 2. Monitor Workflow Execution  
- Open the n8n UI at [http://localhost:5678](http://localhost:5678)  
- Navigate to **Workflows > model-training-v1.n8n**  
- Check for "Success" status in the node execution logs  

### 3. Retrieve Results  
- Embeddings and metadata are stored in your Postgres database with PGVector support.  
- Training data is exported to Google Sheets for integration into Koa's fine-tuning notebooks (see [Notebooks](https://github.com/KoaResearchGroup/notebooks)).  

---

## 📌 Key Features  
✅ **Automated Data Ingestion** from Google Drive  
✅ **Text Cleaning & Chunking** for AI training  
✅ **Vector Embedding Generation** using Ollama  
✅ **Metadata Tracking** in Postgres (with PGVector)  
✅ **Scalable Processing** for large document batches  

---

## 🤝 Contributing  
This workflow is part of Koa Research Group's open-source ecosystem. You can:  
- Improve the chunking logic or add support for new file formats  
- Extend embedding generation to include multi-modal data (e.g., images)  
- Optimize PostgreSQL queries for faster retrieval  

For contributions, submit a pull request to [Koa Research Group/n8n](https://github.com/KoaResearchGroup/n8n).  

---

## 📄 License  
This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.  

---

## 🔗 Related Projects   
- [Notebooks](https://github.com/KoaResearchGroup/notebooks): Fine-tuning scripts for AI models  
- [Koa Research Group Website](https://koaresearch.group): Learn more about our mission  

---

**Questions?** Reach out to the Koa team at koaresearch.group or contribute directly to this repository! 🚀