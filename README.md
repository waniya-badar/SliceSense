# SliceSense
SliceSense - An AI-powered assistant designed to answer user queries about a pizza restaurant by analyzing realistic customer reviews. Built using LangChain, Ollama, and Chroma (FAISS), it allows you to chat in real time with an intelligent model that responds based on insights extracted from a CSV of pizza reviews. This is a fun yet powerful example of domain-specific Retrieval-Augmented Generation (RAG) using LLMs.

### Features:
- LLM-Powered Q&A using Ollama
- Semantic search using vector embeddings via Chroma
- Loads and embeds real pizza reviews from CSV
- Real-time chat interface in the terminal
- Fully local, no OpenAI API key needed

### Tech Stack:
| Tool                          | Purpose                                                  |
| ----------------------------- | -------------------------------------------------------- |
| **LangChain**                 | LLM chaining and orchestration                           |
| **Ollama**                    | Local LLM inference (`llama3.2` and `mxbai-embed-large`) |
| **Chroma (LangChain Chroma)** | Vector store to embed and retrieve reviews               |
| **Pandas**                    | CSV reading                                              |
| **Python**                    | Core logic and CLI                                       |

### Set up Ollama:
Make sure Ollama is installed and models are pulled:

ollama run llama3:instruct
ollama pull mxbai-embed-large

### Running the App:
python main.py


Ask your question (q to quit):
> Is the pizza spicy?

Answer:
The reviews mention the pepperoni pizza has a bit of a kick...

### How It Works:
- Reviews are embedded using mxbai-embed-large into a Chroma vector store.
- When you ask a question:
1. It retrieves the top 5 semantically relevant reviews.
2. The question + reviews are fed to llama3.2 using a prompt.
3. The LLM generates a context-aware answer.

### Notes:
You can replace realistic_restaurant_reviews.csv with your own restaurant data, just keep columns: Title, Review, Rating, and Date.

The app is designed to re-use the vector store once it's created, so startup is faster next time.
