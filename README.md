# tensorflow-detect-logo

Example Machine Learning project using:

* Python 2.7.x
* TensorFlow 1.13.x


## Installation

Install dependencies using:

    virtualenv env
    source env/bin/activate
    pip install -r requirements.txt


## Usage

Retrain the model using:

    python -m src.retrain \
        --bottleneck_dir=dist/bottlenecks \
        --how_many_training_steps=500 \
        --model_dir=dist/models \
        --summaries_dir=dist/summaries \
        --output_graph=dist/retrained_graph.pb \
        --output_labels=dist/retrained_labels.txt \
        --architecture="mobilenet_0.50_224" \
        --image_dir=src/images \
        --learning_rate=0.005


Test the model using:

    python -m src.classify \
        --graph=dist/retrained_graph.pb  \
        --labels=dist/retrained_labels.txt \
        --image=src/images_test/o1.jpg

Run monitor and inspecting tool:

    tensorboard --logdir dist/summaries &

View training stats:

    http://localhost:6006/

Stop monitoring and inspecting:

    pkill -f "tensorboard"


## Results

| Old Logo                          | New Logo                          |
:----------------------------------:|:----------------------------------:
![](https://github.com/kmturley/tensorflow-detect-logo/raw/master/src/images_test/o1.jpg)  |  ![](https://github.com/kmturley/tensorflow-detect-logo/raw/master/src/images_test/n1.jpg)
| Evaluation time (1-image): 0.285s | Evaluation time (1-image): 0.261s |
| old (score=0.92341)               | new (score=0.98649)               |
| new (score=0.07659)               | old (score=0.01351)               |


## Directory structure

    /dist           --> Compiled files after training (bottlenecks, models, summaries, graphs, labels)
    /src            --> Source files


## Contact

For more information please contact kmturley
