## Vietnamese speech recognition with Wav2Vec and Wav2letter
This repository contains ready-to-use software for automatic speech recognition. After downloading pre-trained models and installing dependencies, you can quickly make predictions by using:

```
from stt import Transcriber

transcriber = Transcriber(w2letter = '/path/to/wav2letter', w2vec = 'resources/wav2vec.pt', 
                          am = 'resources/am.bin', tokens = 'resources/tokens.txt', 
                          lexicon = 'resources/lexicon.txt', lm = 'resources/lm.bin',
                          temp_path = './temp',nthread_decoder = 4)

transcriber.transcribe(['data/audio/VIVOSSPK01_R001.wav','data/audio/VIVOSSPK01_R002.wav'])
```

## Technical overview
Techniques and sofware were used to build the model:
 - [Speech2vec](https://arxiv.org/abs/1904.05862) for feature extraction. It use self-supervised learning and unlabeled data to learn contextual representation of raw audio, significant outperforms traditional MFCC in a low-resource setting.
 - [wav2letter](https://arxiv.org/pdf/1609.03193.pdf): for training Acoustic Modeling
 - [kenlm](https://github.com/kpu/kenlm): for training Language Modeling.
