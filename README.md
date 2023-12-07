# Create Dataset:
One video for “real” faces `"/videos/fake.mp4"` and another for “fake/spoofed” faces `"/videos/real.mp4"`


# Install environment


```
conda create -n liveness python=3.8
conda activate liveness
pip install -r requirements.txt
```
# Running
```

# data pre-process (Split videos to images)
python gather_examples.py -i ./videos/fake.mp4 -o ./dataset/fake -d ./face_detector -c 0.9 -s 1 -f 0
python gather_examples.py -i ./videos/real.mp4 -o ./dataset/real -d ./face_detector -c 0.9 -s 1 -f 0

# train model (Resnet50)
python train_liveness.py -d ./dataset -m liveness.model -l le.pickle


# run liveness model on web cam (demo)
python webcam.py -m liveness.model -l le.pickle -d ./face_detector -c 0.5

```


