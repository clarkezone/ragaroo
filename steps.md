# Phases of RAG

1. Scenario: Print help for CLI
2. Scenario: Run CLI generate with path to PDF as args.  Result: stats displayed
3. Scenario: Run CLI query with path to PDF and openai key as args.  Repl loop requesting input and printing result

files:
- vectordb
- generate
- chat

## Generate DB
- Parse CLI args to get path to PDF
- Parse PDF: is there a lib?
- Chunk parsed text: langchain (library) has a chunker for PDF, may have a reader
- Convert chunks to tokens: (open AI) (tiktoken)
- Generate embedding vector: call model (open AI) 
- Store chunks and embedding vectors in memory: (write this)
- Sort vectors by ID for efficient lookup
- Persist in memory representation to file
- Exit printing stats

## Query / chat
- parse arguments to extract file path to load and openAI key
- Load file and deserialize to in-memory representation
- repl loop
- handle previous context
- check token limits
- convert query text to chunks
- convert chunks to tokens
- generate embedding vector from tokens (tiktoken)
- perform COSINE similarity search between query embedding vector and all memory vectors
- Sort results by proximity
- For top n results, look up chunks
- Create grounding for OpenAI
- Call OpenAI with ?custom prompt? and grounding as query
- Print result(s)
