# LangGraph Workflow Orchestration

This project aims to show a LangGraph based workflow orchestration leveraging LangChain and OpenAI models for multi node conversational AI tasks. The system routes user queries dynamically to different specialized nodes (RAG, Web Crawl, LLM) based on intent classification, validates responses, and retries if needed.
---

## Features

- **Supervisor Node:** Classifies user queries into categories (`AI`, `Web`, `Not Related`) using a prompt-based LLM classifier.
- **Router:** Routes queries to appropriate nodes:
  - **RAG Node:** Retrieves relevant context from a PDF document knowledge base and answers user questions.
  - **Web Crawl Node:** Searches the web using Tavily API for real-time results.
  - **LLM Node:** Directly answers user questions using the OpenAI LLM.
- **Validator Node:** Validates the generated answers, detects weak or uninformative responses, and triggers retries.
- **Re-router:** Handles retry logic to prevent dead ends or poor answers.
- **Final Node:** Returns the validated response.

---

## Setup

### Prerequisites

- Python 3.8+
- OpenAI API key
- Tavily API key (for web search)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/langgraph-workflow-orchestration.git
   cd langgraph-workflow-orchestration
   ```

2. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3. Create a .env file in the root directory and add your API keys:
    ```env
    OPENAI_API_KEY=your_openai_api_key_here
    TAVILY_API_KEY=your_tavily_api_key_here
    ```

4. Prepare your PDF documents in the ./data folder for RAG-based retrieval.

## Workflow Overview
- Input: User query in state["messages"].
- Supervisor: Classifies the query to route it.
- Router: Sends query to RAG, Web Crawl, or LLM nodes based on classification.
- Answer Generation: Each node generates an answer based on its logic.
- Validator: Checks answer quality, and requests retries if needed.
- Final: Returns the validated answer.

## Code Highlights
- Uses LangChain and LangGraph for building modular NLP workflows.
- Uses Chroma vector store for PDF document retrieval.
- Integrates OpenAI models for both classification and generation.
- Leverages TavilySearchResults for web crawling API integration.
- Demonstrates conditional routing and retry logic using state graph.

## Contact
For any questions or clarifications, please contact Raza Mehar at [raza.mehar@gmail.com].


