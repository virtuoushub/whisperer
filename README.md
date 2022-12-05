
# whisperer

Go from raw audio files to a text-audio dataset automatically with OpenAI's Whisper.

## Summary

This repo takes a directory of audio files and converts them to a text-audio dataset. The dataset is split on silences and the text is transcribed using OpenAI's Whisper tool. The output is a text-audio dataset that can be used for training a speech-to-text model. Currently the code only supports single speaker audio files.

The dataset structure is as follows:

```
/dataset
      |
      | -> metadata.txt
      | -> /wavs
              | -> audio1.wav
              | -> audio2.wav
              | ...
```
## Configuration


### How to use:

1. Clone the repo
``` 
git clone https://github.com/miguelvalente/whisperer.git
```
2. Install the dependencies
```
conda create -n whisperer python=3.11
conda activate whisperer
pip install -r requirements.txt
```
3. Create data folder and move audio files to it
```
mkdir data
mkdir data/audio_files 
```
4. Run the main file
```
python main.py
```

5. Use the ```AnalyseDataset.ipynb``` notebook to visualize the distribution of the dataset

### Using Multiple-GPUS

The code automatically detects how many GPU's are available and distributes the audio files in ```data/audio_files_wav``` evenly across the GPUs.
The automatic detection is done through ```nvidia-smi```. If you want to make the available GPU's explicit you can set the environment variable ```CUDA_AVAILABLE_DEVICES```.  

### Configuration

Modify `config.py` file to change the parameters of the dataset creation.

## To Do

- [ ] Speech Diarization


## Acknowledgements

 - [AnalyseDataset.ipynb adapted from coqui-ai example](https://github.com/coqui-ai)
 - [OpenAI Whisper](https://github.com/openai/whisper)
