# Computer-Vision-Project

The goal of this project was develop an LBP implementation in order to perform a Face Recognition.  

This project was developed for [Computer Vision](http://people.unica.it/giovannipuglisi/didattica/insegnamenti/?mu=Guide/PaginaADErogata.do;jsessionid=CBB39621933B1A5C549359BBEFDCA119.jvm1?ad_er_id=2017*N0*N0*S2*26520*20168&ANNO_ACCADEMICO=2017&mostra_percorsi=S&step=1&jsid=CBB39621933B1A5C549359BBEFDCA119.jvm1&nsc=ffffffff0909189545525d5f4f58455e445a4a42378b) course at [University of Cagliari](http://corsi.unica.it/informatica), supervised by prof. [Giovanni Puglisi](http://people.unica.it/giovannipuglisi/).

For more information about ELBP read the original paper at this link: [Extended local binary patterns for texture classification](https://www.sciencedirect.com/science/article/pii/S0262885612000066).



# Project structure

This project has the following structure

```
Computer-Vision-Project
│   README.md
│   main.py    
│
└─── algorithms
│    	LBP.py
|
└─── _datasets
│   	YaleFaces.zip
|		YaleFaces_small.zip
|
└─── model
|
└─── utils
│   	dataset.py
│   	utils.py
```

In the `algorithms` folder you can find the basic LBP implementation and the ExtendedLBP implementation. 

In the `dataset` folder there are the zip of the dataset used to test the code. You can add here your dataset.

In the `model` folder, the script store the training data values, in order to perform the prediction without traing the classifier again. 

In the `utils` folder there are some helper function.

# Execute 

First of all you have to unzip the YaleFaces.zip in the same folder. 

You can launch the `python main.py` with the following parameters: 

```shell
--dataset datasetName
--algorithm LBP
--training
--histEq
--output

```

By default launching only `python main.py` the script use LBP algorithm with YaleFaces dataset without training (loading from model folder). If there are not model in your model folder you must user `--training`. 
`--histEq` is helpful because perform an histogram equalization before calculating the LBP.
If `--output` is setted the script will produce inside `./datasets/your_chosen_algorithm_/your_chosen_dataset/` the PNG of the LBP calculated for each image.

#### Example

`python main.py --dataset YaleFaces --algorithm LBP`

`python main.py --algorithm ELBP --training`

# Benchmark and classification

Below you will find the results I obtained using my PC (Dell XPS 15 9550, with Intel i7 6700HQ Skylake @ 2.60GHz)

For the classification task I've used `LinearSVM`

| Dataset         | LBP time     | Training time | Testing time | Average Accuracy |
| --------------- | ------------ | ------------- | ------------ | ---------------- |
| YaleFaces       | ≈ 31 seconds | ≈ 33.1        | ≈ 37         | ≈ 0.98           |
| YaleFaces_small | ≈ 4 seconds  | ≈ 4 seconds   | ≈ 4 seconds  | ≈ 0.99           |

| Dataset         | ELBP time | Training time | Testing time | Average Accuracy |
| --------------- | --------- | ------------- | ------------ | ---------------- |
| YaleFaces       |           |               |              |                  |
| YaleFaces_small |           |               |              |                  |

![](http://i67.tinypic.com/msykqq.png)

# Dependencies

In order tu run, test and modify the source code you must install the following package.

```shell
#CV2
sudo apt-get install python-opencv

#PIP
sudo apt-get install python-pip
pip install Pillow

# SKLEARN
pip install -U scikit-learn

sudo apt-get install build-essential python3-dev python3-setuptools 
sudo apt-get install python3-numpy python3-scipy
sudo apt-get install libopenblas-dev

# DLIB
sudo apt-get install build-essential cmake
sudo apt-get install libgtk-3-dev
sudo apt-get install libboost-all-dev


sudo pip install scikit-image
sudo pip install dlib
```

