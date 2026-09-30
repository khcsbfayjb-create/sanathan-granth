# Ask Sanatan — AI architecture

## Goal
Make the experience conversational like ChatGPT while keeping answers anchored to the selected Hindu text.

## Request shape
{
  "message": "Explain this verse in simple language",
  "textId": "bhagavad-gita",
  "chapter": 2,
  "passageId": "2.47",
  "language": "en",
  "conversationId": "..."
}

## Retrieval
Store each passage as a searchable record with text ID/title, chapter number/title, passage number, original source text, transliteration, verified translation where licensing permits, metadata/tags, and an embedding for semantic search.

Retrieve the smallest useful set of passages. If a user asks about a selected verse, that verse should be the primary context.

## Generation rules
- Clearly label generated explanations as explanations.
- Never fabricate a Sanskrit quotation.
- Do not present a model interpretation as the original scripture.
- Include source references when retrieval produced sources.
- If sources are insufficient, say that the answer needs more source context.
- For disputed interpretations, identify that multiple traditions/commentaries exist instead of pretending there is only one interpretation.
- Keep language simple unless the user asks for scholarly detail.

## Voice
Use browser/mobile TTS for an initial version. Later add server-generated audio for Sanskrit pronunciation and multilingual narration after selecting licensed voice/audio resources.

## Future API
POST /api/chat
POST /api/explain
GET /api/texts
GET /api/texts/:id/chapters
GET /api/texts/:id/chapters/:chapter
GET /api/passages/:id
POST /api/search
POST /api/tts
POST /api/conversations
GET /api/conversations/:id
POST /api/conversations/:id/messages
GET /api/sources/:id
