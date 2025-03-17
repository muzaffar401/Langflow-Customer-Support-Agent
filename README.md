# Customer Support Agent - Langflow & Streamlit

## Overview
This project integrates **Langflow** for customer support automation using a chatbot powered by **Astra DB**, **OpenAI**, and **Streamlit**. The chatbot processes user queries, retrieves relevant information from a database, and provides structured responses.

## Features
- **Natural Language Processing (NLP)**: Understands and responds to user queries.
- **Vector Search with Astra DB**: Fetches relevant documents based on embeddings.
- **FAQ Handling**: Uses a predefined FAQ system to answer common queries.
- **Manager Agent**: Directs responses based on context.
- **Streamlit UI**: Provides a user-friendly interface for interaction.

---

## Workflow Breakdown (Based on Langflow Diagram)

### 1. **User Input**
   - The user enters a query in the **Streamlit UI**.
   - This query is passed as a message to the Langflow backend.

### 2. **Processing the Query**
   - The **Prompt Component** structures the input query into a structured format.
   - If the query matches a predefined **FAQ**, a direct response is given.

### 3. **Database Querying**
   - If the answer isn't available in FAQs, the system searches **Astra DB**.
   - The **Astra DB Tool** retrieves relevant documents using vector embeddings.
   - The data is processed and converted into a human-readable format.

### 4. **Manager Agent Execution**
   - The **Manager Agent** assigns tasks to retrieve and process information.
   - It selects whether to use FAQs, Database Search, or Contextual Analysis.
   
### 5. **Context Lookup (Advanced Queries)**
   - For more complex queries, **Context Lookup Agent** is engaged.
   - It refines responses using additional context from documents.

### 6. **Response Handling & Display**
   - The processed response is sent to the **Chat Output** component.
   - The response is displayed in the **Streamlit UI** for the user.

---

## Setup Instructions

### 1. **Clone the Repository**
```bash
$ git clone https://github.com/muzaffar401/Langflow-Customer-Support-Agent.git
$ cd Langflow-Customer-Support-Agent
```

### 2. **Install Dependencies**
This project uses `Poetry` for dependency management.
```bash
$ poetry install
```
Or using `pip`:
```bash
$ pip install -r requirements.txt
```

### 3. **Set Environment Variables**
Create a `.env` file and add:
```
API_TOKEN=your_api_token_here
```

### 4. **Run the Streamlit App**
```bash
$ streamlit run app.py
```

---

## API Integration
This project calls Langflow APIs for execution. The request structure is:

### API Endpoint:
```
POST https://api.langflow.astra.datastax.com/lf/{LANGFLOW_ID}/api/v1/run/{ENDPOINT}
```

### Request Payload:
```json
{
    "input_value": "User message here",
    "output_type": "chat",
    "input_type": "chat"
}
```

---

## Future Enhancements
- **Multilingual Support**
- **Voice Command Integration**
- **Chat History Storage**

### License
This project is licensed under the MIT License.

