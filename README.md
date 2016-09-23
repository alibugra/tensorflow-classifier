# TensorFlow Image Classifier
TensorFlow is a an open source library for numerical computation, specializing in machine learning applications. You will learn how to install and run TensorFlow on a single machine, and will train a simple classifier to classify images of flowers.

Following dependencies must be installed:
- Python 2.7
- TensorFlow
- Docker

## Installing Docker
You can find Docker for Linux installation instructions on the [Docker site](https://docs.docker.com/engine/installation/).

## Get the set of flower photos
```
$ cd $HOME
$ mkdir tensorflow-classifier
$ cd tensorflow-classifier
$ curl -O http://download.tensorflow.org/example_images/flower_photos.tgz
$ tar xzf flower_photos.tgz
```

## Start Docker
```
$ docker run -it -v $HOME/tensorflow-classifier:/tensorflow-classifier gcr.io/tensorflow/tensorflow:latest-devel
```

## Training Inception
```
$ cd /tensorflow
$ git pull
$ python tensorflow/examples/image_retraining/retrain.py \
--bottleneck_dir=/tensorflow-classifier/bottlenecks \
--how_many_training_steps 500 \
--model_dir=/tensorflow-classifier/inception \
--output_graph=/tensorflow-classifier/retrained_graph.pb \
--output_labels=/tensorflow-classifier/retrained_labels.txt \
--image_dir /tensorflow-classifier/flower_photos
```

## Predict an image
```
$ python /tensorflow-classifier/label_image.py /tensorflow-classifier/flower_photos/roses/2414954629_3708a1a04d.jpg
```
