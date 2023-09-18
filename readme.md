# mAP (mean Average Precision)

This code will evaluate the performance of your neural net for object recognition.
In practice, a **higher mAP** value indicates a **better performance** of your neural net, given your ground-truth and set of classes.

## Citation

This project was developed for the following paper and the [source code](https://github.com/Cartucho/mAP), please consider citing them.

```bibtex
@INPROCEEDINGS{8594067,
  author={J. {Cartucho} and R. {Ventura} and M. {Veloso}},
  booktitle={2018 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)}, 
  title={Robust Object Recognition Through Symbiotic Deep Learning In Mobile Robots}, 
  year={2018},
  pages={2336-2341},
}
```

## Modification
This project is following Cartucho's mAP project. Thanks for his contribution.
- 1.Considering the detection network sometimes use the scaled image as input, the size of output is not always same as input. We provide the code for detection results followed by **scale operation**.
- 2.Original code request the format of ground-truth files and results files strictly. We do some modifications for allow the files containing extra information which may be used during the post process.


## Quick-start

Step by step:

  1. [Create the ground-truth files](#create-the-ground-truth-files)
  2. Copy the ground-truth files into the folder **input/ground-truth/**
  3. [Create the detection-results files](#create-the-detection-results-files)
  4. Copy the detection-results files into the folder **input/detection-results/**
  5. a）Run the code directly:
         ```
         python main_scale.py
         ```
     
     b) if the prediction results has been scaled, run the code:
     
         ```
         python main_scale.py --gt-h 'gtH' --gt-w 'gtW' --pred-h 'predH' --pred-w 'predW'
         ```


Optional (if you want to see the **animation**):

  6. Insert the images into the folder **input/images-optional/**

#### Create the ground-truth files

- Create a separate ground-truth text file for each image.
- Use **matching names** for the files (e.g. image: "image_1.jpg", ground-truth: "image_1.txt").
- In these files, each line should be in the following format:
    ```
    <class_name> <left> <top> <right> <bottom> [<difficult>] [other args]
    ```
- The `difficult` parameter is optional, use it if you want the calculation to ignore a specific detection.
- E.g. "image_1.txt":
    ```
    tvmonitor 2 10 173 238
    book 439 157 556 241
    book 437 246 518 351 difficult
    pottedplant 272 190 316 259
    ```
#### Create the detection-results files

- Create a separate detection-results text file for each image.
- Use **matching names** for the files (e.g. image: "image_1.jpg", detection-results: "image_1.txt").
- In these files, each line should be in the following format:
    ```
    <class_name> <confidence> <left> <top> <right> <bottom> [other args]
    ```
- E.g. "image_1.txt":
    ```
    tvmonitor 0.471781 0 13 174 244
    cup 0.414941 274 226 301 265
    book 0.460851 429 219 528 247
    chair 0.292345 0 199 88 436
    book 0.269833 433 260 506 336
    ```
