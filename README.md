# Face Recognization with MTCNN and FaceNet

## Set up

### Set up code and file

```

git clone git@github.com:DngBack/FaceRecog.git

cd FaceRecog

```

### Set up and Create Some Folder

```
<!-- Create Models Folder  -->
mkdir Models 

<!-- Create DataSet Folder -->
mkdir DataSet 

```

#### Set up dataset

If you want to run and identify any character, put their photos into a folder, put the character's name and prepare according to the architecture below.

Folder Strucure

```

-- DataSet 
--- FaceData
---- precessed
---- raw 
----- NguyenVanA
----- DuongXuanB

```

#### Set up pretrain models

Dowload pre train models from here: [20180402-114759.pb](https://drive.google.com/file/d/1EXPBSXwTaqrSC0OhUdXNmKSh9qJUQ55-/view)

After that, extract it to Models

### Set up env with colab

```

conda create -n facenet python==3.10

conda activate facenet

cd FaceRecog

pip install -r requirements.txt
```

## Run File

```

<!-- Extract face -->
python3 src/align_dataset_mtcnn.py  Dataset/FaceData/raw Dataset/FaceData/processed --image_size 160 --margin 32  --random_order --gpu_memory_fraction 0.25

<!-- Train Dataset -->
python3 src/classifier.py TRAIN Dataset/FaceData/processed Models/20180402-114759.pb Models/facemodel.pkl --batch_size 1000

<!-- Run Camera -->
python3 src/face_rec_cam.py 
```
