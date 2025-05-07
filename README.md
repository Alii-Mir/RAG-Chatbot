# Software Environment:

![Example](https://github.com/user-attachments/assets/5d608cfb-f7a5-407e-b0e9-9067eb454f82)



# 📚 PDF Q&A System with Groq Streaming LLM API

This project is an interactive **PDF Q&A system** designed to allow users to upload PDF documents, index their contents, and query the information contained within them. Powered by Groq's streaming Large Language Model (LLM) API, the system generates accurate, contextually relevant answers derived exclusively from the uploaded PDFs. If a question cannot be answered based on the provided documents, the system responds with "I do not know," ensuring transparency and reliability. The application is delivered through an intuitive Gradio interface, making it accessible and easy to use for individuals regardless of technical expertise.

---

## 🌟 Key Features

- **📄 PDF Upload and Indexing**  
  Users can upload one or multiple PDF files. The system extracts text, segments it into chunks (size: 800 characters, overlap: 100 characters), and embeds these chunks using the `intfloat/e5-large-v2` sentence transformer model. The resulting embeddings are stored in a FAISS vector database for rapid and efficient retrieval.

- **🔍 Intelligent Question Answering**  
  Users can pose questions about the PDF content. The system retrieves the most relevant text chunks from the vector store and feeds them into Groq's LLM (`meta-llama/llama-4-scout-17b-16e-instruct`) to generate precise answers. If the information is absent from the PDFs, it returns "I do not know."

- **🤖 Groq API Integration**  
  The system leverages Groq's streaming LLM API, enabling real-time, context-aware responses based on the indexed document content.

- **🖥️ Gradio-Powered Interface**  
  A sleek, user-friendly web interface built with Gradio allows seamless interaction, including PDF uploads, knowledge base creation, question input, and detailed logging of operations.

- **⚡ Efficient Processing**  
  Text embeddings are computed on the available hardware (CPU or CUDA), ensuring optimal performance tailored to the user's environment.

---

## 🛠️ How It Works

The system operates through a streamlined pipeline that transforms raw PDF data into actionable answers. Here's a step-by-step breakdown:

1. **PDF Processing**  
   Uploaded PDFs are parsed using `PyPDFLoader`, with `PyPDF2` validating and extracting text from each page.

2. **Text Chunking**  
   The extracted text is divided into manageable chunks using `RecursiveCharacterTextSplitter` (chunk size: 800, overlap: 100), preserving context across segments.

3. **Embedding Generation**  
   Each chunk is converted into a vector representation using the `intfloat/e5-large-v2` sentence transformer model. These embeddings are computed on the available device (CPU or CUDA) for flexibility and speed.

4. **Vector Storage**  
   The embeddings are indexed in a FAISS vector database, optimized for fast similarity searches across high-dimensional data.

5. **Question Processing**  
   When a user submits a question, it is embedded using the same `intfloat/e5-large-v2` model. A similarity search identifies the most relevant chunks from the vector store.

6. **Answer Generation**  
   The retrieved chunks, along with the user's question, are sent to Groq's LLM via the streaming API. The LLM crafts an answer based solely on the provided context, ensuring fidelity to the document content.

---

## 🧰 Technologies Used

The system integrates a robust stack of modern tools and libraries:

- **LangChain**: Manages document loading, text splitting, and vector store operations.  
- **FAISS**: Provides efficient similarity search capabilities for vectorized data.  
- **Sentence Transformers**: Generates high-quality embeddings with the `intfloat/e5-large-v2` model.  
- **PyPDF2 & PyPDFLoader**: Handles PDF parsing and text extraction.  
- **Groq**: Powers answer generation via the `meta-llama/llama-4-scout-17b-16e-instruct` LLM.  
- **Gradio**: Delivers an interactive, web-based user interface.  
- **Torch**: Facilitates device-agnostic computation (CPU/CUDA support).

---

## 📖 Usage Instructions

Getting started with the PDF Q&A system is straightforward:

1. **Enter Your Groq API Key**  
   Input your Groq API key into the designated field to authenticate with the LLM service.

2. **Upload PDF Documents**  
   Use the file upload component to select and upload one or more PDF files for processing.

3. **Build the Knowledge Base**  
   Click the "Build Knowledge Base" button to initiate text extraction, chunking, embedding, and indexing. Progress and any issues are logged in real-time for transparency.

4. **Ask Questions**  
   Type your question into the text box and click "Get Answer." The system will retrieve relevant information from the PDFs and display the LLM-generated response.

---

## 💡 Potential Use Cases

This system is versatile and can be applied in various contexts:

- **Research Assistance**  
  Rapidly extract key information from lengthy academic papers, technical reports, or whitepapers.

- **Educational Support**  
  Enable students to query textbooks, lecture notes, or study materials for quick comprehension.

- **Business Intelligence**  
  Analyze contracts, manuals, or internal documents to uncover actionable insights efficiently.

- **Personal Knowledge Management**  
  Create a searchable archive of personal PDFs for quick reference and question-based retrieval.

---

## 🚀 Future Improvements

The system has significant potential for enhancement:

- **Broader File Format Support**  
  Expand compatibility to include DOCX, TXT, Markdown, and other document types.

- **Enhanced Retrieval Techniques**  
  Incorporate hybrid search or reranking algorithms to improve the precision of retrieved chunks.

- **Multi-Language Capabilities**  
  Add support for processing and answering questions in multiple languages, broadening accessibility.

- **Persistent Knowledge Bases**  
  Implement user authentication and storage to save and manage multiple indexed datasets.

- **Performance Optimization**  
  Explore advanced caching or batch processing to accelerate indexing and query response times.

---

## ⚙️ Technical Details

- **Chunk Configuration**: Text is split with a chunk size of 800 characters and an overlap of 100 characters to maintain context.  
- **Embedding Model**: `intfloat/e5-large-v2` ensures high-quality vector representations.  
- **LLM Model**: Groq's `meta-llama/llama-4-scout-17b-16e-instruct` drives answer generation.  
- **Hardware Flexibility**: Supports both CPU and CUDA-enabled GPUs via Torch integration.

This PDF Q&A system combines cutting-edge AI with a practical, user-centric design, offering a powerful tool for interacting with document-based knowledge.

