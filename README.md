# DLC Toolbox
A library of scripts that are handy when processing DeepLabCut data

## `preprocess.py`
A handy python script that 
1. converts `.mkv` output of OBS to DLC acceptable `.mp4` format.
2. Extract uncompressed audio in `.wav` format
3. Analyze and output a CSV file of the most significant sound stimuli at each time step.

**Note** 
- this script by default apply a highpass (lowcut) filter of 5000Hz as it was intended to screen for ultrasound stimuli.
- Because this script uses ffmpeg, run the script in command line interface so that you can interact with ffmpeg when necessary. (e.g. overwrite request)

**Usage**: 
```
usage: preprocess.py [-h] -i INPUT [INPUT ...] -o OUTPUT [-v] [-r] [--verbose-ffmpeg] [--highpass-hz HIGHPASS_HZ] [--no-skip] [--no-highpass] [--just-mp4]
                     [--target-frames TARGET_FRAMES]

This script help preparing videos for audio analysis by extracting audio from video files and saving them as .wav files. It also extracts pitch and decibel information from the audio and saves them as .csv files.

optional arguments:
  -h, --help            show this help message and exit
  -i INPUT [INPUT ...], --input INPUT [INPUT ...]
                        Input file(s) or directory(ies)
  -o OUTPUT, --output OUTPUT
                        Output directory
  -v, --verbose         Enable verbose mode
  -r, --resample        Enable resampling
  --verbose-ffmpeg      Enable verbose mode for ffmpeg
  --highpass-hz HIGHPASS_HZ
                        Highpass filter frequency
  --no-skip             Do not skip existing .csv (overwrite)
  --no-highpass         Do not apply highpass filter
  --just-mp4            Do not extract and analyze audio from video files, just convert them to .mp4 for DeepLabCut
  --target-frames TARGET_FRAMES
                        Target frame count for resampling

Example usage: python preprocess.py -i /path/to/video.mp4 -o /path/to/output_dir -v 
 OR: python preprocess.py -i /path/to/video_dir -o /path/to/output_dir -v 
 OR: python preprocess.py -i /path/to/audio.wav -o /path/to/output_dir -v
```
