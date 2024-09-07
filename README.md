# Voice Synthesizer - TTSStreamer

This project is a Text-to-Speech (TTS) synthesizer that clones voices based on short audio clips, such as famous personalities like Morgan Freeman. It generates speech in the style of the target voice using a custom trained model and allows real-time streaming of generated audio with buffering. The project utilizes `pydub` for audio processing and `TTS` models for speech synthesis.

## Features

- **Clone Voice:** Synthesize a target voice based on a short audio clip.
- **Streaming Audio Playback:** Play generated audio with real-time buffering.
- **Adjustable Speed & Language:** Modify the speed and language of the generated audio.
- **GPU Support:** Leverage CUDA for faster audio generation using GPUs.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/voice-synthesizer.git
   cd voice-synthesizer
   ```

2. Install dependencies:
   ```bash
   pip install pydub soundfile torch TTS
   ```

3. Download or prepare your pre-trained TTS model and place it in the `XTTS-v2` directory.

## Usage

### Initialize TTSStreamer

The `TTSStreamer` class handles the loading of the TTS model and the generation of audio from text.

```python
from tts_streamer import TTSStreamer

tts_streamer = TTSStreamer(
    model_path="XTTS-v2", 
    config_path="XTTS-v2/config.json", 
    vocab_path="XTTS-v2/vocab.json"
)
```

### Stream Text as Audio

Provide text input to stream audio with real-time playback.

```python
text = """
A series of extracts from Middle English texts of different dates and types...
"""

tts_streamer.stream_audio_with_buffering(
    text, 
    language="en", 
    speed=1.3, 
    speaker_path="XTTS-v2/samples/morgan_freeman.wav",
    fireup_delay=5.0
)
```

This will generate audio in the cloned voice style, buffer it, and play it with a 5-second delay before starting playback.

## Project Structure

- `TTSStreamer`: Main class that handles model loading, text processing, and audio generation.
- `XTTS-v2/`: Directory for storing model files, configuration, and vocabulary.
- `samples/`: Example audio files used to clone voices.

## Requirements

- Python 3.8+
- [PyDub](https://github.com/jiaaro/pydub)
- [TTS](https://github.com/coqui-ai/TTS)
- GPU (CUDA support recommended)

## Example

Here’s an example of the generated output using Morgan Freeman’s voice:

- **Original Clip**: `samples/morgan_freeman_original.mp3`
- **Cloned Voice**: `samples/morgan_freeman_cloned.mp3`

## License

This project is licensed under the MIT License.

## Acknowledgements

Special thanks to the developers of the [Coqui TTS](https://github.com/coqui-ai/TTS) framework for providing open-source tools for text-to-speech synthesis.
