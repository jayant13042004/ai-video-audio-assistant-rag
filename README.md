# AI Video & Audio Assistant — RAG

A Streamlit application that converts YouTube videos and local audio/video files into transcripts, summaries, action items, key decisions and open questions. It also allows users to ask questions about the transcript using Retrieval-Augmented Generation (RAG).

## Features

- Accepts YouTube URLs and local audio/video files.
- Extracts audio and converts it to WAV.
- Splits audio into chunks for transcription.
- Uses **OpenAI Whisper** for English transcription.
- Uses **Sarvam AI** for Hinglish speech-to-text translation.
- Generates session titles and summaries.
- Extracts action items, key decisions and open questions.
- Uses **Mistral** to answer questions based on transcript context.
- Provides a Streamlit interface with processing status and chat history.

## Architecture

```text
YouTube URL / Local Media
          |
     Audio Extraction
          |
   WAV Conversion + Chunking
          |
      Transcription
     /             \
  Whisper         Sarvam AI
     \             /
      Transcript Text
             |
   Summary and Extraction
             |
    Embeddings + ChromaDB
             |
       Semantic Retrieval
             |
        Mistral LLM
             |
     Contextual Answers
```

The RAG pipeline retrieves the four most relevant transcript chunks before generating an answer. The model is instructed to answer using the supplied transcript context.

## Technology Stack

Python, Streamlit, OpenAI Whisper, Sarvam AI API, LangChain, Mistral, ChromaDB, Pydub, yt-dlp and FFmpeg.

## Installation

```bash
git clone https://github.com/jayant13042004/ai-video-audio-assistant-rag.git

cd ai-video-audio-assistant-rag

python -m venv .venv

# Windows
.venv\Scripts\activate

pip install -r requirements.txt

streamlit run app.py
```

**Dependency note:** Verify that the repository contains a valid, lowercase `requirements.txt` before using this installation command. Add the actual dependencies used by the project if the file is missing.

Install FFmpeg separately and ensure it is available on your system PATH.

## Environment Variables

Create a `.env` file in the project root:

```env
MISTRAL_API_KEY=your_mistral_api_key
SARVAM_API_KEY=your_sarvam_api_key
```

- `MISTRAL_API_KEY` is used by the Mistral language model.
- `SARVAM_API_KEY` is required for Hinglish transcription.
- Never commit API keys or `.env` files to GitHub.

## Limitations

- Transcription quality depends on audio clarity, language and background noise.
- Long recordings require additional processing time.
- Hinglish transcription depends on Sarvam API availability and limits.
- Answer quality depends on transcription and retrieved context.
- Model and API usage may incur costs or rate limits.

## Author

**Jayant Jagtap**

[GitHub](https://github.com/jayant13042004)
