# Restaurant RAG Chatbot 🍽️💬

An intelligent Q&A chatbot for Eleven Madison Park restaurant built using Retrieval-Augmented Generation (RAG) technology. This project demonstrates how to create a context-aware chatbot that can answer questions about a restaurant using its website data.

## Overview

This chatbot uses state-of-the-art natural language processing to provide accurate, source-cited answers about Eleven Madison Park. It combines LangChain, OpenAI embeddings, ChromaDB vector storage, and a user-friendly Gradio interface to deliver an interactive Q&A experience.

## Features

- **Intelligent Document Retrieval**: Uses semantic search to find relevant information from restaurant data
- **Source Citations**: Provides answers with references to original sources
- **Vector Database**: Efficient similarity search using ChromaDB
- **Interactive UI**: Clean, user-friendly Gradio interface
- **Context-Aware Responses**: Leverages OpenAI's language models for natural conversation
- **Flexible Document Processing**: Automatic text chunking with overlap for better context retention

## Technologies Used

- **LangChain** (v0.1.0): Framework for building LLM applications
- **OpenAI API**: Embeddings and language model
- **ChromaDB**: Vector database for semantic search
- **Gradio**: Web interface for user interaction
- **Python 3.x**: Core programming language

## Project Structure

```
restaurant-rag-chatbot/
├── restaurant-rag-chatbot.ipynb    # Main Jupyter notebook
├── eleven_madison_park_data.txt    # Restaurant data source
└── readme.md                        # Project documentation
```

## Installation

### Prerequisites

- Python 3.8 or higher
- OpenAI API key

### Setup Instructions

1. **Clone the repository** (or download the files)

2. **Install required packages:**
   ```bash
   pip install langchain==0.1.0 langchain-community==0.0.10 langchain-core==0.1.10 langchain-openai==0.0.2 openai chromadb tiktoken gradio python-dotenv
   ```

3. **Set up OpenAI API key:**
   - Create a `.env` file in the project root
   - Add your OpenAI API key:
     ```
     OPENAI_API_KEY=your_api_key_here
     ```
   - Alternatively, if using Google Colab, store it in Colab secrets

## Usage

### Running the Notebook

1. Open `restaurant-rag-chatbot.ipynb` in Jupyter Notebook or Google Colab

2. Run the cells sequentially to:
   - Install dependencies
   - Configure OpenAI client
   - Load and process restaurant data
   - Create embeddings and vector store
   - Initialize the RAG chain
   - Launch the Gradio interface

3. Once the Gradio interface launches, you can ask questions like:
   - "What are the different menu options and prices?"
   - "Who is the head chef?"
   - "What is Magic Farms?"
   - "Is Eleven Madison Park plant-based?"
   - "What are the career opportunities?"

### How It Works

1. **Data Loading**: Restaurant website data is loaded from `eleven_madison_park_data.txt`

2. **Text Splitting**: Documents are split into chunks (1000 characters with 150-character overlap)

3. **Embedding Creation**: Each chunk is converted to vector embeddings using OpenAI's embedding model

4. **Vector Storage**: Embeddings are stored in ChromaDB for efficient retrieval

5. **Query Processing**: User questions are:
   - Converted to embeddings
   - Matched against stored vectors
   - Top relevant chunks are retrieved
   - Sent to OpenAI with context for answer generation

6. **Response**: The chatbot provides an answer with source citations

## Configuration Options

### Key Parameters

- **Chunk Size**: 1000 characters (adjustable in `RecursiveCharacterTextSplitter`)
- **Chunk Overlap**: 150 characters (ensures context continuity)
- **Retrieval Count**: Top 3 documents (k=3)
- **Temperature**: 1.3 (controls response creativity)
- **Chain Type**: "stuff" (combines all retrieved documents)

### Customization

You can modify the chatbot behavior by adjusting:
- `temperature` parameter in the LLM initialization (0 for factual, 2 for creative)
- `k` value in retriever configuration (number of documents to retrieve)
- `chunk_size` and `chunk_overlap` in text splitter

## Data Source

The chatbot uses data from Eleven Madison Park's website, including:
- Restaurant information
- Career opportunities
- Gift cards
- Press and accolades
- Accessibility statement
- Menu details

## Example Queries

```
Q: What kind of food does Eleven Madison Park serve?
A: [Generated answer with plant-based cuisine information]
Sources: eleven_madison_park_data.txt

Q: What different menus are offered?
A: [Generated answer about menu options]
Sources: eleven_madison_park_data.txt
```

## Limitations

- Responses are limited to information in the provided data file
- Requires active OpenAI API key and credits
- Response quality depends on data completeness
- Context window limitations may affect very long documents

## Future Enhancements

- [ ] Add support for multiple restaurant data sources
- [ ] Implement conversation history
- [ ] Add multi-turn dialogue capabilities
- [ ] Include image processing for menu items
- [ ] Deploy as a web application
- [ ] Add caching for common queries
- [ ] Support for multiple languages

## Dependencies

```
langchain==0.1.0
langchain-community==0.0.10
langchain-core==0.1.10
langchain-openai==0.0.2
openai
chromadb
tiktoken
gradio
python-dotenv
```

## Contributing

Feel free to fork this project and adapt it for your own restaurant or business Q&A needs. The architecture is flexible and can be extended to other domains.

## License

This project is provided as-is for educational and demonstration purposes.

## Acknowledgments

- Eleven Madison Park for the restaurant data
- LangChain for the RAG framework
- OpenAI for embeddings and language models
- Gradio for the user interface

---

**Note**: This is a demonstration project. For production use, consider implementing proper error handling, rate limiting, cost controls, and security measures.
