# Wav2Lip Lip Sync Implementation

## Project Overview

This repository contains an implementation of the Wav2Lip model for lip-syncing. The project can generate realistic lip-sync videos by synchronizing a target face video with a given audio track.

## Demo Results

The final video shows a face speaking the following script with synchronized lip movements:

> Namaste Mathangi! My name is Anika, and I'm here to guide you through managing your credit card dues. Mathangi, as of today, your credit card bill shows an amount due of INR 5,053 which needs to be paid by 31st December 2024. Missing this payment could lead to two significant consequences: First, a late fee will be added to your outstanding balance. Second, your credit score will be negatively impacted, which may affect your future borrowing ability. Make your payment by clicking the link here... Pay through UPI or bank transfer. Thank you!

### Wav2Lip Model

[![Wav2Lip Demo](https://img.youtube.com/vi/v=KfXImErd8rE/0.jpg)](https://www.youtube.com/watch?v=KfXImErd8rE)

### Wav2Lip + GAN Model

[![Wav2Lip Demo](https://img.youtube.com/vi/v=KfXImErd8rE/0.jpg)](https://www.youtube.com/watch?v=KfXImErd8rE)

## Project Structure

```
Wav2Lipsync/
├── Wav2Lip/                 # Main Wav2Lip implementation
│   ├── checkpoints/         # Pre-trained model weights
│   ├── face_detection/      # Face detection models
│   ├── results/             # Generated output videos
│   └── inference.py         # Main inference script for lip-syncing
├── sample_data/             # Input data
│   ├── video.mp4            # Input face video
│   ├── audio2.mp3           # Generated TTS audio with Indian accent
│   └── audio.mp3            # Original audio file
└── Yubi_Assignment.ipynb    # Jupyter notebook with the full implementation
```

## Implementation Details

This project combines several key components:

1. **Face Video Input**: A video containing a face that will be animated to match the audio.

2. **Text-to-Speech (TTS)**: Using Google's Text-to-Speech API with Indian accent (`tld='co.in'`) to generate natural-sounding speech for the notification script.

3. **Wav2Lip Model**: Two pre-trained models were tested:

   - `wav2lip.pth`: Standard model for lip syncing
   - `wav2lip_gan.pth`: GAN-enhanced model for potentially higher quality results

4. **Face Detection**: Using the S3FD face detector to locate and track faces in the input video.

## How It Works

1. The input face video is processed to extract frames.
2. The audio file is analyzed to extract speech features.
3. The Wav2Lip model synchronizes the lip movements of the face with the speech in the audio.
4. The final video is generated with the synchronized lips and the original audio.

## Technical Implementation

The implementation leverages Google Colab's GPU capabilities for faster processing. Key libraries used include:

- **gTTS**: For generating Indian-accented TTS audio
- **librosa**: For audio processing (version 0.9.1 specifically)
- **PyTorch**: For running the deep learning models
- **OpenCV**: For video processing
- **ffmpeg**: For final video encoding

## How to Run

To run the Google Colab notebook, make sure you download and upload the pre-trained models in your Google Drive inside a folder called `Wav2Lip`.

1. Run the Jupyter notebook `Yubi_Assignment.ipynb` in Google Colab with GPU runtime.

## Results Comparison

Two models were tested:

1. **Standard Wav2Lip**: Faster processing but slightly lower quality.
2. **Wav2Lip + GAN**: Higher quality results with better realism, but slower processing time.

The final output video can be found in the `Wav2Lip/results/` directory.
