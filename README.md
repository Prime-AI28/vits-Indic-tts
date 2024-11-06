# How to use
(Suggestion) Python == 3.7
## Clone this repository
```sh
git clone https://github.com/Prime-AI28/vits-Indic-tts.git
```
## Choose cleaners
- Fill "text_cleaners" in config.json
- Edit text/symbols.py

## Install requirements
```sh
pip install -r requirements.txt
```
## Create datasets
### Single speaker
"n_speakers" should be 0 in config.json
```
path/to/XXX.wav|transcript
```
- Example
```
sanskrit/sp002/sp002-002155.wav|1|दिवसमुखोचितम् दिवसमुखे प्रातःकाले उचितम् करणीयम् विधिम् अनुष्ठानम् अवसाय्य समाप्य
```
### Mutiple speakers
Speaker id should start from 0 
```
path/to/XXX.wav|speaker id|transcript
```
- Example
```
sanskrit/sp002/sp002-002155.wav|1|दिवसमुखोचितम् दिवसमुखे प्रातःकाले उचितम् करणीयम् विधिम् अनुष्ठानम् अवसाय्य समाप्य
```
## Preprocess
If you have done this, set "cleaned_text" to true in config.json
```sh
# Single speaker
python preprocess.py --text_index 1 --filelists path/to/filelist_train.txt path/to/filelist_val.txt

# Mutiple speakers
python preprocess.py --text_index 2 --filelists path/to/filelist_train.txt path/to/filelist_val.txt
```
## Build monotonic alignment search
```sh
cd monotonic_align
python setup.py build_ext --inplace
cd ..
```
## Train
```sh
# Single speaker
python train.py -c <config> -m <folder>

# Mutiple speakers
python train_ms.py -c <config> -m <folder>
```
## Inference
### Online
See [inference.ipynb](inference.ipynb)

