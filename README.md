# AI Video & Audio Assistant (RAG)

An end-to-end **RAG** application that turns YouTube videos and local audio/video files into summaries, action items, decisions, open questions, and answers to your questions.

## Pipeline
```
YouTube / local file → Transcription → Chunking → Embeddings → ChromaDB → Retrieval → Mistral → Answer
```
- **Transcription:** Whisper for English; Sarvam AI for Hinglish-to-English
- **Retrieval:** transcript chunking, embeddings, vector storage in ChromaDB, semantic search
- **Generation:** Mistral produces summaries, action items, decisions, open questions, and contextual answers
- **Interfaces:** Streamlit app and CLI

## Tech stack
Python, LangChain, Whisper, ChromaDB, Mistral, Sarvam AI, Streamlit

## Run locally
```bash
git clone https://github.com/jayant13042004/ai-video-audio-assistant-rag.git
cd ai-video-audio-assistant-rag
pip install -r requirements.txt
cp .env.example .env      # add MISTRAL_API_KEY and SARVAM_API_KEY
streamlit run [app_file].py
```

## Demo
(Add a screenshot: `![demo](images/demo.png)`)

## Evaluation (add if you run it)
| Test | Result |
|---|---|
| [20] questions on [N] videos, top-k retrieval hit rate | [x]% |

## Limitations
- Transcription quality limits answer quality, especially on noisy audio.
- Long videos take time to transcribe.

## Author
Jayant Jagtap · [LinkedIn](https://www.linkedin.com/in/jayantjagtap/)
