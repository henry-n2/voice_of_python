<div align="center">
  <img src="https://raw.githubusercontent.com/henry-n2/voice_of_python/main/Voice_of_python_logo.png" width="250" alt="Voice of Python Logo">
</div>

# Voice of Python
> Offline Multilingual Voice Bot Library for Python 🎙️

[![PyPI Version](https://img.shields.io/pypi/v/voice_of_python.svg)](https://pypi.org/project/voice-of-python/)
[![Python Versions](https://img.shields.io/pypi/pyversions/voice_of_python.svg)](https://pypi.org/project/voice-of-python/)
[![License](https://img.shields.io/github/license/henry-n2/voice_of_python.svg)](https://github.com/henry-n2/voice_of_python/blob/main/LICENSE)

`voice_of_python` is a robust Python library providing offline multilingual speech recognition and text-to-speech (TTS) capabilities. Powered by the **Vosk** toolkit for precise offline speech-to-text and **pyttsx3** for offline TTS, it seamlessly supports multiple languages with automatic language detection.

---

## 🌟 Key Features

- **Offline Processing**: Complete offline speech-to-text using Vosk models—no APIs or internet required.
- **Audio Inputs**: Record audio directly from the microphone or process existing WAV files.
- **Auto-Language Detection**: Smartly identifies spoken languages using `langid`.
- **Text-to-Speech (TTS)**: Synthesizes responses in the detected language's voice (if locally available).
- **CPU Optimized**: Fully functional on CPU, making it perfect for local, privacy-centric applications.
- **LLM Ready**: Purpose-built for easy integration with large language models (LLMs) and custom chatbots.

---

## 📦 Installation

Ensure you have installed the required dependencies. You can install the package directly from PyPI:

```bash
pip install voice_of_python
```
*(Alternatively, to install dependencies manually: `pip install vosk langid pyttsx3 sounddevice numpy soundfile`)*

> **Note:** Download and extract [Vosk models](https://alphacephei.com/vosk/models) for your supported languages separately to a local folder.

---

## 🚀 Quick Start

### 1. Initialize the Voice Bot

Provide the paths to your downloaded Vosk models:

```python
from voice_of_python import MultiLingualVoiceBot

model_paths = {
    "en": "/path/to/vosk-model-en-us-0.22",
    "hi": "/path/to/vosk-model-small-hi-0.22"
}

bot = MultiLingualVoiceBot(model_paths)
```

### 2. Record & Transcribe Live Audio

Listen from the microphone, detect language, and transcribe text:

```python
text, lang_code = bot.record_and_transcribe(record_duration=5)

print(f"Detected language: {lang_code}")
print(f"Recognized text: {text}")
```

### 3. Integrate with an LLM (Example)

Pass the transcribed `text` to your backend model (like OpenAI, LLaMA, etc.) to generate a conversational response.

```python
# Example response from an LLM
reply_text = "यहाँ आपका उत्तर है"
```

### 4. Speak the Reply

Respond to the user naturally in the detected language:

```python
bot.speak_text(reply_text, lang_code)
```

### 5. Process Existing Audio Files

Alternatively, handle pre-recorded audio files:

```python
audio_file = "user.wav"
reply_text = "Thank you for your question."

bot.process_audio_and_reply(audio_file, reply_text)
```

---

## 📖 API Reference

### `MultiLingualVoiceBot(model_paths: dict, sample_rate: int = 16000)`
Initializes the bot.
- `model_paths`: A dictionary mapping language codes to their respective local Vosk model paths (e.g., `{"en": "/path"}`).
- `sample_rate`: Sampling rate for audio processing (default is 16000 Hz).

### `record_and_transcribe(record_duration: int = 5) -> tuple[str, str]`
Records audio directly from the default microphone.
- **Returns**: A tuple containing `(recognized_text, language_code)`.

### `process_audio_and_reply(audio_input: Union[str, np.ndarray], reply_text: str)`
Transcribes provided audio, detects language, and immediately speaks the provided reply.
- `audio_input`: A file path to a WAV file or a raw numpy array.
- `reply_text`: The text response to be spoken aloud.

### `speak_text(text: str, lang_code: str)`
Reads out the text using the system's text-to-speech engine.
- `text`: Text to synthesize.
- `lang_code`: The language code to select the proper voice.

---

## 🤝 Contributing

We welcome contributions! Please feel free to open issues, submit pull requests, or discuss new features on [GitHub](https://github.com/henry-n2/voice_of_python).

---

## 📚 Acknowledgements

This project builds upon several amazing open-source libraries:
- **[Vosk](https://alphacephei.com/vosk/)**: For robust offline speech recognition.
- **[pyttsx3](https://pyttsx3.readthedocs.io/en/latest/)**: For text-to-speech conversion.
- **[langid](https://github.com/saffsd/langid.py)**: For accurate language identification.

---

## 💬 Support

If you encounter any bugs or have questions, please [open an issue on GitHub](https://github.com/henry-n2/voice_of_python/issues).

<div align="center">
  <i>Enjoy building multilingual, offline voice-enabled applications with <b>voice_of_python</b>!</i>
</div>
