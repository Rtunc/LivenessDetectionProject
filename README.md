
```
conda create -n liveness python=3.8
conda activate liveness
pip install -r requirements.txt
```

```
# data pre-process
python gather_examples.py -i ./videos/fake.mp4 -o ./dataset/fake -d ./face_detector -c 0.9 -s 1 -f 0
python gather_examples.py -i ./videos/real.mp4 -o ./dataset/real -d ./face_detector -c 0.9 -s 1 -f 0
python gather_examples.py -i ./videos/mask.mp4 -o ./dataset/mask -d ./face_detector -c 0.9 -s 1 -f 0

# train model
python train_liveness.py -d ./dataset -m liveness.model -l le.pickle

# run liveness model on test video
python liveness_demo.py -m liveness.model -l le.pickle -d ./face_detector -c 0.5
press "q" to quit

# run liveness model on web cam
python webcam.py -m liveness.model -l le.pickle -d ./face_detector -c 0.5

```


