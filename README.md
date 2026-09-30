# Sanatan Granth

Sanatan Granth is a conversational, chapter-wise digital library for Hindu spiritual texts.

## Product
- ChatGPT-style **Ask Sanatan** conversation interface
- Chapter-wise reading for Bhagavad Gita and expandable support for Vedas, Upanishads, Ramayana, Mahabharata and Puranas
- Simple-language explanations while clearly separating source text from generated explanation
- Text-to-speech reading for passages
- Source-grounded answers: every AI response should identify the text/chapter/passage used when source retrieval is available
- Future features: bookmarks, reading progress, multilingual explanations, audio, semantic search and conversation history

## AI architecture
The production backend should use a retrieval-augmented generation (RAG) pipeline:

1. User asks a question or selects a passage.
2. Search the structured scripture corpus for relevant passages.
3. Send only the retrieved source passages plus the user's question to the model.
4. Instruct the model to explain in simple language, distinguish interpretation from source text, and avoid inventing quotations.
5. Return an answer with source references: text → chapter → passage.

The UI is deliberately provider-agnostic so the AI backend can later use an OpenAI-compatible API or another model provider without redesigning the reader.

## Local development

```bash
npm install
npm run dev
```

## Repository structure

- `src/main.jsx` — app UI and navigation
- `src/styles.css` — visual system
- `data/gita.json` — chapter metadata and initial passage corpus
- `docs/AI_ARCHITECTURE.md` — RAG and safety/content-grounding design
