# Lossless-Binary-Image-Denoising

## What is denoising? 
![alt text](https://github.com/peeeebeeeeeee/Lossless-Binary-Image-Denoising/blob/main/content/Denoising.jpg?raw=true)

## Introduction
The common solution for denoising a binary image or any image for that matter is with the help of morphologyEx(). But, does it remove all the noise pixels under a threshold? It surely can, but to generate all the possible kernels for a particular threshold can be an easy task initially. But as the threshold is increased, it gives you a hard time figuring out all the possible kernels and then applying them to the image. Training a CNN model any better? There are chances of distorting or losing the current pixels. So, isn't it better to get to the elementary level? I mean the pixels themselves.

### What is an island? 
A group of connected 1s forms an island. For example, the below matrix contains 4 islands.
![alt text](https://github.com/peeeebeeeeeee/Lossless-Binary-Image-Denoising/blob/main/content/FindNumberOfIslands.png?raw=true)

## How it works? 
Considering a threshold parameter from the user, we remove those island pixels whose area is equal to or lesser than the threshold. We go pixel by pixel, checking whether the island area is lesser than the given threshold. If so, we ignore them. If not, we mark all the pixels in that area so that we ignore in the future upcoming pixel checks. At the end, we have a 2-d array full of noise pixels for a given image. Later we compare with the original image and remove these noise pixels. Thus, we are not disturbing the current pixels by any sort, ensuring a lossless denoising.

## Optimisation
A parallel distribution of tasks into pools has been implemented, so that images are segmented into smaller frames and denoised seperately. Indeed, this speeds up the whole process. The user can set a parameter for the minimum size of the frame to be denoised seperately, making the whole process more customisable.

## Test Results

*The following image has been denoised at a threshold of 20. Go through image folders for results from threshold 1-20.*

![alt text](https://github.com/peeeebeeeeeee/Lossless-Binary-Image-Denoising/blob/main/content/test1.png?raw=true)
![alt text](https://github.com/peeeebeeeeeee/Lossless-Binary-Image-Denoising/blob/main/content/test2.png?raw=true)

## Tools Used
- OpenCV
- pathos
- numpy

