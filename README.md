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
        --image_dir=src/images


Test the model using:

    python -m src.classify \
        --graph=dist/retrained_graph.pb  \
        --labels=dist/retrained_labels.txt \
        --image=src/images_test/test1.jpg


## Directory structure

    /dist           --> Compiled files after training (bottlenecks, models, summeries, graphs, labels)
    /src            --> Source files


## Contact

For more information please contact kmturley
