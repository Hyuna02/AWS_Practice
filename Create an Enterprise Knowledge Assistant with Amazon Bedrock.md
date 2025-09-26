# Create an Enterprise Knowledge Assistant with Amazon Bedrock

## 🧠 Concept
In this practice lab you’ll build an **enterprise knowledge assistant** using a **RAG (Retrieval-Augmented Generation)** workflow so an LLM can answer questions grounded in your company’s documents. You will:

- Upload documents to **Amazon S3**
- Enable models in **Amazon Bedrock**
- Create a **Bedrock Knowledge Base**
- Use **Amazon OpenSearch Serverless (Vector Engine)** as the vector store
- Ask **sales-related questions** to validate accuracy and references

## 🎯 Practice Lab Goals
- Upload documents to an Amazon S3 bucket  
- Enable models on the Amazon Bedrock console  
- Create an Amazon Bedrock knowledge base  
- Use Amazon OpenSearch Serverless as a vector store  
- Test knowledge base accuracy by asking the model sales-related questions  

---

## 🧩 Services & Key Concepts

### 1) Amazon S3 (Document Storage)
- Durable, scalable **object storage** for PDFs, DOCX, TXT, CSV, etc.  
- Serves as the **data source** for the Knowledge Base.  
- Recommended: **Versioning**, **server-side encryption** (SSE-S3 or **SSE-KMS**), clear bucket/IAM policies.

### 2) Amazon Bedrock (LLMs & Knowledge Base)
- Fully managed, **serverless** access to multiple foundation models.  
- **Enable Models**: In the console, choose generation and embedding models and accept terms.  
- **Knowledge Base**: Handles document ingestion, chunking, **embeddings**, retrieval, and **retrieve-and-generate** orchestration (RAG).

### 3) Amazon OpenSearch Serverless — Vector Engine (Vector Store)
- Managed **vector similarity search** (ANN) for embeddings.  
- No cluster management; scales with traffic and storage.  
- Use encryption (KMS), network access policies, and collection-level security.

### 4) RAG (Retrieval-Augmented Generation)
- The LLM is “grounded” with retrieved document **chunks** to improve factuality, reduce hallucinations, and provide **citations**.

### 5) Embeddings & Chunking
- **Embeddings** map text to high-dimensional vectors; semantically similar text is nearby.  
- **Chunking** (e.g., 512–1000 tokens with overlap) improves recall and context continuity.

### 6) IAM & Security
- Apply **least privilege** with IAM roles/policies between Bedrock, S3, and OpenSearch Serverless.  
- Use **KMS encryption**, **CloudTrail** for auditing, and **VPC endpoints/PrivateLink** if needed.

---

## 🏗️ Architecture Overview
1. **S3**: Upload sales documents (price lists, promos, product guides, FAQs).  
2. **Bedrock Knowledge Base**: Connect S3 → create embeddings → index into **OpenSearch Serverless**.  
3. **Query**: Console/SDK/app sends a question → KB retrieves relevant chunks → LLM generates an answer with references.

![Create an Enterprise Knowledge Assistant](https://github.com/Hyuna02/AWS_Practice/blob/main/CreateanEnterpriseKnowledgeAssistant.png)

