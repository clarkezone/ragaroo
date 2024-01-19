# Phases of RAG

Scenario: Run CLI generate against a document

## Generate
- Parse PDF
- Chunk parsed text
- Convert chunks to tokens
- Generate embedding vector (tiktoken)
- Store chunks and embedding vectors in memory
- Persist in memory representation to file
- Exit printing stats

## Query
- Load file and deserialize to in-memory representation
- convert query text to chunks
- convert chunks to tokens
- generate embedding vector from tokens (tiktoken)
- perform COSINE similarity search between query embedding vector and all memory vectors
- Sort results by proximity
- For top n results, look up chunks
- Create grounding for OpenAI
- Call OpenAI with ?custom prompt? and grounding as query
- Print result(s)
