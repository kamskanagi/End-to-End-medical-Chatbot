# End-to-End Medical AI Chatbot

A sophisticated medical AI chatbot powered by Retrieval-Augmented Generation (RAG) technology that provides intelligent medical information and assistance. The system combines advanced language models with a comprehensive medical knowledge base to deliver accurate, contextual responses.

## Features

- **RAG-Powered Responses**: Uses Retrieval-Augmented Generation for accurate, context-aware medical answers
- **Vector Database Integration**: Pinecone vector database for efficient medical document retrieval
- **Modern Web Interface**: Professional, responsive chat interface with medical-themed design
- **Multiple AI Providers**: Supports both Groq and OpenAI language models
- **Semantic Search**: HuggingFace embeddings for intelligent document matching
- **Health Monitoring**: Built-in health check endpoints for system monitoring
- **Medical Safety**: Automatic disclaimers and safety warnings for medical advice

## Architecture

- **Backend**: Flask web application with comprehensive error handling
- **AI Models**: Groq (Meta Llama) or OpenAI for language generation
- **Vector Store**: Pinecone for medical document storage and retrieval
- **Embeddings**: HuggingFace sentence transformers for semantic understanding
- **Frontend**: Modern HTML/CSS/JavaScript chat interface

## Prerequisites

- Python 3.8 or higher
- Git
- API Keys for:
  - Pinecone (vector database)
  - Groq or OpenAI (language models)

## Installation

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd End-to-End-medical-Chatbot
   ```

2. **Create a virtual environment**

   Using Conda (Recommended):

   ```bash
   conda create -n medicalbot python=3.8 -y
   conda activate medicalbot
   ```

   Or using Python venv:

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**

   Create a `.env` file in the root directory:

   ```env
   PINECONE_API_KEY=your_pinecone_api_key
   GROQ_API_KEY=your_groq_api_key
   ```

5. **Set up vector database** (First time only)

   Run the indexing script to populate Pinecone with medical documents:

   ```bash
   python store_index.py
   ```

## Usage

### Starting the Application

Run the Flask server:

```bash
python app.py
```

The application will be available at: `http://127.0.0.1:8081`

### Available Endpoints

- `/` - Main chat interface
- `/get` - Medical query processing API (POST)
- `/health` - System health check

### Using the Chat Interface

1. Open your browser and navigate to `http://127.0.0.1:8081`
2. Type your medical question in the chat input
3. Receive AI-powered responses with relevant medical context
4. All responses include medical disclaimers for safety

## Development

### Project Structure

```
├── app.py                 # Main Flask application
├── store_index.py        # Vector database setup
├── requirements.txt      # Python dependencies
├── src/
│   ├── helper.py         # Utility functions for document processing
│   └── prompt.py         # System prompts for AI models
├── templates/
│   └── chat.html         # Chat interface template
├── static/
│   ├── style.css         # Interface styling
│   └── script.js         # Frontend functionality
├── Documents/            # Medical documents for indexing
└── research/             # Experimental notebooks
```

### Adding Medical Documents

1. Place PDF documents in the `Documents/` folder
2. Run `python store_index.py` to update the vector database
3. Restart the application to use the updated knowledge base

### Configuration

Key configuration variables in `app.py`:

- `MEDICAL_VECTOR_INDEX_NAME`: Pinecone index name
- `SIMILARITY_SEARCH_RESULTS_COUNT`: Number of documents to retrieve
- `LLM_TEMPERATURE`: Model creativity (0 for deterministic responses)
- `GROQ_MODEL_NAME`: Groq model identifier
- `FLASK_HOST` and `FLASK_PORT`: Server configuration

## Health Monitoring

Check system status:

```bash
curl http://127.0.0.1:8081/health
```

Response includes status of all system components:

- Embeddings model
- Document retriever
- Language model
- RAG chain

## Safety and Disclaimers

- All responses include medical disclaimers
- System is designed for educational purposes only
- Users are advised to consult healthcare professionals for medical decisions
- No personal health information is stored or logged

## Troubleshooting

### Common Issues

1. **Port conflicts**: Change `FLASK_PORT` in `app.py` if port 8081 is in use
2. **API key errors**: Verify `.env` file configuration and API key validity
3. **Document retrieval issues**: Ensure Pinecone index is properly created with `store_index.py`
4. **Model loading errors**: Check internet connection and API service status

### Logs

The application provides comprehensive logging. Check console output for detailed error information and system status updates.

## License

This project is intended for educational and research purposes. Ensure compliance with medical information regulations in your jurisdiction.

## Disclaimer

This medical AI chatbot is for educational and informational purposes only. It should not be used as a substitute for professional medical advice, diagnosis, or treatment. Always seek the advice of qualified healthcare providers with questions about medical conditions.
