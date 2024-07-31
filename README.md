# LocSAR
It is a pytorch implementation for LocSAR which can generate complex SAR ship image at a specified location.
We will add to this project when our paper is published.
## Setup
## Datasets
We re-labeled the HRSID dataset, using rotated boxes for all targets. Noted that land and sea usually have horizontal edges, we used a rotated frame with an angle of 0 in the labeling. Besides, in order to balance the number of ships with other classes of targets in the dataset, we added another 530 images of only land and sea targets using data enhancement methods, which will allow the model to better learn the features of other targets (especially land). In total, the dataset contains 2362 images with rotated box.

The datasets will be pubilshed after the paper is pubished.
### Prepare data
We provide two label formats. They are txt format and voc format. When you unzip it, its format is shown as follows.
```
|——Multicata HRSID
  |——images # 2362 images
    |——['.jpg']
    |——  ...
    |——['.jpg']
  |——annotations
    |——voc
      |——['.xml']
      |—— ...
      |——['.xml']
    |——txt
      |——['.txt']
```
By the way, we use 0 is for land, 1 is for sea and 2 is for ship.
There is only one text file in the "txt" folder, where each line is formatted as follows:**path rotatedbox1(cx,cy,w,h,angle) catagory1 rotatedbox2(cx,cy,w,h,angle) catagory2 ...** just like the image below shows.

![image](https://github.com/waeada/LocSAR/blob/main/images/image1.png)



### Dataset visualization 
![image](https://github.com/waeada/LocSAR/blob/main/images/image3.png)

## Visualization generates results
With our new labled dataset, our model achieves an amazing results. We provide a comparison image among (a) visual mask map, (b) real image and (c) LocSAR.

![image](https://github.com/waeada/LocSAR/blob/main/images/image5.png)


We are most proud of the model's feature learning for terriestrial targets. In order to show the power of our model, we used 200 pure land images to train it as well, the results after training are shown below. Guess which one is real and which one is fake?
![image](https://github.com/waeada/LocSAR/blob/main/images/image4.png)
where (a) is fake image generated by our model and (b) is gorund truth.

## Display UI
In order to speed up the labeling process, a simple user interface has been developed. Through it, the researchers can specify the category and positional coordinates of the target to obtain the desired SAR image. Firstly, use “**confirm input**” to end the input of information about a target. Then use “**show rotated box**” to display the position of the currently entered target. Finally, use “**generate image**”  to generate the fake image using the entered target information. Both the label and the fake image are saved automatically. We also provide "**delete**" to clear the information of the previous target.
We provide some examples of inputs as well as their outputs.
![image](https://github.com/waeada/LocSAR/blob/main/images/image6.png)

![image](https://github.com/waeada/LocSAR/blob/main/images/image7.png)

![image](https://github.com/waeada/LocSAR/blob/main/images/image9.png)

![image](https://github.com/waeada/LocSAR/blob/main/images/image11.png)


