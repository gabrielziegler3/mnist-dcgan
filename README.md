# PyTorch DCGNA MNIST Generator

## Download the data

Download MNIST dataset to your data folder. 

```
wget https://github.com/myleott/mnist_png/blob/master/mnist_png.tar.gz -P data
```

Go to `data/` and decompress the data.
```
cd data/
tar -xvf mnist_png.tar.gz
```

The folder structure will look like this
![](https://miro.medium.com/max/375/1*ikfrJldwpQ3lItLhhirgjQ.png)

## Usage

Pull the used docker image

```
docker pull gabrielziegler/rocmpytorch
```

Run the container adding your GPU if you have one with ROCM or CUDA.

```
docker run -it -v `pwd`:/data --privileged --rm --device=/dev/kfd --device=/dev/dri --group-add video gabrielziegler
```

When inside the container, change directory to the mounted path

```
cd /data
```

Now, you're in the right directory, so just run jupyter

```
jupyter-notebook --ip=0.0.0.0 --port=8000 --allow-root --NotebookApp.token='' --no-browser
```

## Performance after 100 epochs

### Discriminator Loss Fake vs Loss Real

<p align="center">
    <img src="./images/Discriminator Loss_Fake.svg" width="400" height="600">
    <img src="./images/Discriminator Loss_Real.svg" width="400" height="600">
</p>

### Generator Loss

<center>
    <img src="./images/Generator Loss.svg" width="500" height="600">
</center>

## Random generated digit sample

<center>
    <img src="./images/mnist_sample.png" width="800" height="600">
</center>
