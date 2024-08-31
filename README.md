# YAI-X-Prevenotics
<!-- HEADER START -->
<!-- src: https://github.com/kyechan99/capsule-render -->
<p align="center"><a href="#">
    <img width="100%" height="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:C0C0C0,50:87CEEB,100:1E90FF&height=220&section=header&fontSize=40&fontColor=ffffff&animation=fadeIn&fontAlignY=40&text=Medical%20Report%20Generation" alt="header" />
</a></p>


<p align="center">
<br>
<a href="mailto:jmme425@yonsei.ac.kr">
    <img src="https://img.shields.io/badge/-Gmail-D14836?style=flat-square&logo=gmail&logoColor=white" alt="Gmail"/>
</a>
<a href="https://www.notion.so/y-ai/PREVENOTICS-548a329b2fc54f65a1d72c5aadb103de?pvs=4">
    <img src="https://img.shields.io/badge/-Project%20Page-000000?style=flat-square&logo=notion&logoColor=white" alt="NOTION"/>
</a>
<a href="https://www.notion.so/y-ai/66e6e1ec8314487d9807730e2c5190c0?pvs=4">
    <img src="https://img.shields.io/badge/-Full%20Report-dddddd?style=flat-square&logo=latex&logoColor=black" alt="REPORT"/>
</a>
</p>
<br>
<hr>
<!-- HEADER END -->

# Implementation for personalized medical report genenration via Medical Large Language Model(LLM) 👩‍💼
<br>Face recognition model for virtual human generation<br>

# Members 👋
<b> <a href="https://github.com/rubato-yeong">김진영</a></b>&nbsp; :&nbsp; YAI 13th&nbsp; /&nbsp; jinyeong1324@yonsei.ac.kr<br>
<b>  <a href="https://github.com/jmjmfasdf">서정민</a></b>&nbsp; :&nbsp; YAI 12th&nbsp; /&nbsp; jmme425@yonsei.ac.kr  <br>
<b> <a href="https://github.com/0914eagle">전희재</a></b>&nbsp; :&nbsp; YAI 12th&nbsp; /&nbsp; 0914eagle@yonsei.ac.kr <br>
<b> <a href="#">고현아</a></b>&nbsp; :&nbsp; YAI 13th&nbsp; /&nbsp; kha9867@yonsei.ac.kr <br>
<b> <a href="https://github.com/1n1ng">조인희</a></b>&nbsp; :&nbsp; YAI 13th&nbsp; /&nbsp; choinh@yonsei.ac.kr <br>
<hr>

# Getting Started 🔥
This project is based on model from [Med42-Llama](https://huggingface.co/m42-health/Llama3-Med42-70B). We would like to acknowledge the contributors and maintainers of that repository for their valuable work.

## Setup

Before installing DeepFace, ensure you have Python 3.5.5 or higher installed. If you want to utilize GPU acceleration, you'll need to install TensorFlow with CUDA support prior to installing DeepFace.

### GPU Installation (Optional)

To enable GPU support, install TensorFlow with CUDA by running:

```bash
pip install tensorflow[and-cuda]
```

### Installation Steps 
To install deepface, follow these steps:

1. Clone the repository:
```bash
git clone https://github.com/JungKH33/face-similarity.git
```

2. Navigate to the cloned directory:
```bash
cd deepface
```
3. Install deepface:
```bash
pip install -e .
```

### Download pretrained models
To use AdaFace, download the ONNX file from [this link](https://drive.google.com/drive/folders/10_FVXnofz0EJh3bbWRoGN84ATHCZ66IE?usp=drive_link) and place it in the `weights/adaface` folder.
You can change the directory if you modify the model_path variable in `deepface/basemodels/AdaFace`.

### Download Datasets 

The dataset we have provided can be downloaded from [this link](https://drive.google.com/drive/folders/1xQKjGDVOKOCC43JnXeyhbQcSug-U5474).

If you want to add a custom dataset, the dataset should be in the following structure:

```
📦 dataset_folder
├─ person_1
│  ├─ image1.jpg
│  ├─ image2.jpg
│  └─ ...
├─ person_2
│  ├─ image1.jpg
│  ├─ image2.jpg
│  └─ ...
└─ person_3
   ├─ image1.jpg
   ├─ image2.jpg
   └─ ...
```

## Usage 

### Calculate Similarity

This script calculates the average similarity between multiple people. If a save path is not specified, it plots the similarity matrix; otherwise, it saves the similarity matrix to the specified path. 
You can run the script with the following command:

```bash
python similarity.py --i <path_to_dataset> --o <path_to_save_directory> --n <number_of_pairs> [--model <model_name>] [--backend <backend_name>] [--metric <metric_name>]
```

You can see the available models and backends by running:
```bash
python similarity.py --help
```

![Similarity Matrix](assets/similarity_matrix.png)

*Figure 1: Example similarity matrix generated by the script. Each cell represents the similarity score between two individuals. Red colors indicate higher similarity, while blue colors indicate lower similarity.*
### Calculate Accuracy

This script calculates the accuracy of a model. You can test different models, backends and thresholds which fits your dataset best.

```bash
python accuracy.py --i <path_to_dataset> --o <path_to_save_directory> --n <number_of_pairs> [--model <model_name>] [--backend <backend_name>] [--metric <metric_name>]
```

You can see the available models, backends, and metrics by running:
```bash
python accuracy.py --help
```

![Accuracy](assets/accuracy.png)

*Figure 2: Example density graph created by the script. It calculates the appropriate threshold and its corresponding accuracy.*

# Building on DeepFace for experiments 🏗️🔬

## DeepFace - [Link](https://github.com/serengil/deepface)
[AdaFace: Quality Adaptive Margin for Face Recognition](https://arxiv.org/abs/2204.00964)
Deepface is a lightweight face recognition and facial attribute analysis (age, gender, emotion and race) framework for python. It is a hybrid face recognition framework wrapping state-of-the-art models: VGG-Face, Google FaceNet, OpenFace, Facebook DeepFace, DeepID, ArcFace, Dlib, SFace and GhostFaceNet.

# Dataset 😊
We made our own datasets to evaluate various combination of model and backend(detection). To evaluate the robustness of each features, we prepared datasets that can represent key features affect face similarity. We picked 6 to 14 identities considering gender, race, age from the datasets below.

## 1. Digiface
([LADN](https://github.com/wangguanzhi/LADN))
Digiface is a collection of over one million diverse synthetic face images for face recognition. There are 720k images with 10K identities containing various face angle, accessories, emotion and hairstyle. We chose 6 identities for fast inference.

# Evaluation result 📋
To find best model combination, we made inference metric of our own. You can test our metric on the datasets above. The model combination we tested is shown as below.
```
model = [
  "VGG-Face",
  "Facenet",
  "Facenet512",
  "OpenFace",
  "DeepFace",
  "DeepID",
  "ArcFace",
  "SFace",
  "AdaFace"
]

backends = [
  'opencv', 
  'ssd', 
  'mtcnn', 
  'retinaface', 
  'mediapipe',
  'yolov8',
  'yunet',
  'fastmtcnn',
]
```

## Skills
<br><img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white"/> 

## Citations
Models
```bibtex
@misc{2408.06142,
Author = {Clément Christophe and Praveen K Kanithi and Tathagata Raha and Shadab Khan and Marco AF Pimentel},
Title = {Med42-v2: A Suite of Clinical LLMs},
Year = {2024},
Eprint = {arXiv:2408.06142},
}
```
Datasets
```bibtex
@inproceedings{hartvigsen2022toxigen,
  title={ToxiGen: A Large-Scale Machine-Generated Dataset for Implicit and Adversarial Hate Speech Detection},
  author={Hartvigsen, Thomas and Gabriel, Saadia and Palangi, Hamid and Sap, Maarten and Ray, Dipankar and Kamar, Ece},
  booktitle={Proceedings of the 60th Annual Meeting of the Association for Computational Linguistics},
  year={2022}
}

@article{jin2020disease,
  title={What Disease does this Patient Have? A Large-scale Open Domain Question Answering Dataset from Medical Exams},
  author={Jin, Di and Pan, Eileen and Oufattole, Nassim and Weng, Wei-Hung and Fang, Hanyi and Szolovits, Peter},
  journal={arXiv preprint arXiv:2009.13081},
  year={2020}
}

```



