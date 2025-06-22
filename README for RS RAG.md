
# 🏡 RealEstate-RAG-Bot

A Retrieval-Augmented Generation (RAG) chatbot designed to intelligently answer real estate-related questions using open-source tools and documents such as contracts, bank statements, lender worksheets, and more. This project uses the **Mistral 7B Instruct** model locally via `llama-cpp-python`, and vectorizes documents with `LlamaIndex`.

## 📌 Key Features

- ⚙️ **RAG pipeline**: Retrieval-Augmented Generation using local vector store
- 🧠 **Mistral 7B** LLM via `llama-cpp-python` (no internet API needed)
- 📄 **PDF support** using `PyMuPDF` for real estate documents like:
  - Contracts
  - Appraisals
  - Paystubs
  - Bank statements
  - Lender fee worksheets
- 🗂️ Custom embedding using `HuggingFace` transformer models

## 🔧 Tech Stack

| Purpose             | Tool/Library                            |
|---------------------|------------------------------------------|
| Model Inference     | `llama-cpp-python`, `Mistral 7B`         |
| Document Ingestion  | `PyMuPDF (fitz)`                         |
| Vector Indexing     | `LlamaIndex`                             |
| Embedding Models    | `llama-index-embeddings-huggingface`     |
| LLM Interface       | `llama-index-llms-llama-cpp`             |
| Notebook Platform   | Google Colab / Jupyter                   |

## 📁 File Structure

```
├── Built RAG with Open Source.ipynb     # Main notebook
├── /content/                            # Folder for real estate PDFs
│   ├── appraisal_report.pdf
│   ├── sample_bank_statement.pdf
│   └── sample_contract.pdf
├── README.md                            # This file
```

## ⚙️ How It Works

1. **Dependencies & Setup**
   - Installs `llama-cpp-python`, `LlamaIndex`, `PyMuPDF`, and HuggingFace embedding packages.
   - Detects and uses GPU via CUDA if available.

2. **Model Download & Setup**
   - Downloads Mistral-7B-Instruct GGUF file from HuggingFace.
   - Loads model locally via `LlamaCPP`.

3. **Document Processing**
   - Extracts text from uploaded PDF files using `PyMuPDF`.
   - Creates `Document` objects for indexing.

4. **Vector Indexing & Querying**
   - Embeds the documents using HuggingFace models.
   - Runs queries using RAG with local LLM to provide answers.

## 💡 Example Use Cases

- 🏘️ “What is the average closing cost in this contract?”
- 📊 “Summarize the appraisal report.”
- 💼 “What deductions appear in this pay stub?”
- 💰 “Show me the monthly payment from this lender worksheet.”

## 🚀 Getting Started

> 💻 Designed for use in Jupyter or Google Colab

1. Clone this repo:
```bash
git clone https://github.com/yourusername/realestate-rag-bot.git
cd realestate-rag-bot
```

2. Install requirements (Colab handles this automatically in notebook):
```bash
pip install llama-cpp-python llama-index pymupdf \
            llama-index-llms-llama-cpp \
            llama-index-embeddings-huggingface
```

3. Add your PDF documents to `/content/`.

4. Run the notebook: `Built RAG with Open Source.ipynb`.

## 🧱 Future Improvements

- [ ] Add a Gradio or Streamlit chatbot interface
- [ ] Expand document support (e.g., `.docx`, `.html`)
- [ ] Dockerize the setup for local deployment
- [ ] Add summarization and document comparison features

## 📝 License

This project is open-source under the [MIT License](LICENSE).
