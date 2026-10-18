# 🗣️ Speaker Agent (free, local)

A voice tutor for **English** and **French**. You speak, it answers out loud, corrects your grammar,
coaches your pronunciation, and at the end gives you a **score, CEFR level (A1–C2), and tips**.

**100% free:** no subscription, no API key.
- The AI is **Gemma 3 4B**, running on your own computer through [Ollama](https://ollama.com).
- Speech recognition and the voice come built into **Chrome / Edge**.
- The server uses only Python's standard library, so there's nothing to `pip install`.

## Run

Double-click **`start.bat`**. It starts Ollama, downloads the model the first time (about 3.3 GB), and opens
http://localhost:8000. Use **Chrome or Edge** and allow the microphone.

Manual alternative: `ollama pull gemma3:4b`, then `python server.py`.

## How to use

1. Choose a language, accent, level, the language for explanations, and a topic.
2. Click 🎤 (or hold **Space**) and speak. The tutor replies by voice.
3. Under each reply you'll see:
   - ✏️ **Corrections**: what you said → a better way to say it, and why
   - 🗣️ **Pronunciation**: words you likely mispronounced, how to say them, 🔊 to hear them
   - 🎯 **Repeat after me**: a practice phrase. Say it and get a word-by-word match score
4. Click **End & get my score** for the report: overall, pronunciation, grammar, vocabulary, fluency
   and comprehension scores, strengths, key mistakes, sounds to practice, and tips.
   Past scores are saved in your browser under "Your progress".

## Speed and quality

On this PC (RTX 2050, 4 GB): first reply about 7 s, normal replies about 20–30 s, the final report about 1 minute.
Turning on "Translate replies" makes replies slower.

A 4B model is small. It is good for conversation practice, but its corrections and scores are
sometimes wrong, so double-check anything that looks surprising. To use another Ollama model:

```
ollama pull qwen2.5:7b
set OLLAMA_MODEL=qwen2.5:7b
start.bat
```

Bigger models give better corrections but are slower on a 4 GB GPU. `gemma3:1b` is faster but weaker.

## How pronunciation feedback works

The browser turns your voice into text and gives a confidence value. When a word is misheard, confidence
is low, or you miss words from a practice phrase, that usually points to a pronunciation problem, and
the tutor uses those signals. It does not do phoneme-level audio analysis.
Note: Chrome's speech recognition is free but needs an internet connection.
