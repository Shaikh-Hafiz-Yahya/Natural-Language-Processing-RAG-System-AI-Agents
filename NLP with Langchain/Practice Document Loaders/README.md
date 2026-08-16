# Lecture 05: Document Loaders — Ingesting Data

Welcome to **Lecture 05** of the **NLP with LangChain** series! This module focuses on **Document Loaders**, the fundamental first step in any Retrieval-Augmented Generation (RAG) pipeline and AI Agent architecture.

---

## 📌 Overview

Large Language Models (LLMs) need access to real-world data stored across various formats and locations. Document Loaders act as the ingestion engine, reading raw data from text files, PDFs, spreadsheets, web pages, and cloud platforms, then wrapping it into a standardized LangChain format.

---

## 🎯 Key Concepts & Features

### 1. The Standard `Document` Object
Regardless of the source, every LangChain loader outputs data into a unified container:
* **`page_content`** (`str`): The raw extracted text.
* **`metadata`** (`dict`): Source attributes such as file path (`source`), page number (`page`), row index (`row`), or web URL.

### 2. Supported Loaders & Implementations

* 📄 **`TextLoader`**: Ingests plain `.txt` and Markdown files as single document units.
* 📑 **`PyPDFLoader`**: Processes multi-page PDFs, converting each page into an independent `Document` object with page metadata.
* 📊 **`CSVLoader`**: Converts structured spreadsheet rows into individual document entries—ideal for product catalogs and databases.
* 🌐 **`WebBaseLoader` & `SitemapLoader`**: Extracts clean text content and titles from web URLs and crawls full sitemaps using BeautifulSoup.
* 🎥 **Cloud & Specialized Loaders**: Pulls transcripts from YouTube videos (`YoutubeLoader`) and interfaces with Google Drive, Notion, and AWS S3.

---

## 🛠️ Selecting the Right PDF Loader

| Loader | Underlying Library | Best For | Speed | Accuracy |
| :--- | :--- | :--- | :--- | :--- |
| **`PyPDFLoader`** | `pypdf` | Simple text PDFs, quick setup | Fast | Good |
| **`PyPDFium2Loader`** | `pypdfium2` | High-volume batch processing | Fastest | Good |
| **`PyMuPDFLoader`** | `PyMuPDF / fitz` | Complex layouts & non-Latin scripts | Fast | Best |
| **`PDFPlumberLoader`** | `pdfplumber` | Tables & structured data extraction | Medium | Excellent for tables |
| **`UnstructuredPDFLoader`** | `unstructured` | Scanned PDFs (requires OCR) | Slow | Great for image PDFs |

---

## 🚀 Environment Setup & Usage

```bash
# Install required dependencies
pip install langchain langchain-community pypdf beautifulsoup4 lxml nest_asyncio tqdm
