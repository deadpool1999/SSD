*Tested on Ubuntu 18.04.* <br/>
<sub>**To reproduce the results please read the README present in the source folder.**</sub>

The total numner of bbox in the Ground truth is 2648. <br/>
We report a 0.78 mAP (3359 bboxs in the prediction) on the given test set with the confidence threshold of 0.25 (we discard any object with a confidence less than 0.25, total numner of bbox in the prediction are: 3359). Furthermore, with a default confidence threshld of 0.01 we achieve 0.82 mAP (4403) but in this case total numner of bbox in the prediction are: 4403. Which means an increase of around 1000 false positive bboxs (Ofcourse we are also discrading some of the true positives too).

**The mAP score is almost same in both the cases but we are reducing around 1000 false positive bboxs in the prediciton.**<br/>


### Dataset preparation steps:
* The dataset for this task is prepared in two steps:
	* First downloading all the required files.
	* Pre-process the data in the required VOC format.
		* Annotated xml file is created in: *source_code/nidhi/VOC2007/Annotatinos*. <br/>
		* Train and test split is created as given for the task:  *source_code/nidhi/VOC2007/ImageSets/Main*. <br/>
		* All the images are put in one folder: *source_code/nidhi/VOC2007/JPEGImages.* <br/>

* Apart from the default data augmentation (normalizing the image, with mean and std), I did not use any augmented data to train the first draft. <br/>

**Detection network used:** A standard [SSD]("https://arxiv.org/pdf/1512.02325.pdf") architecture is used in this implementation. <br/>
* Default parameters used are as mentioned in the Max deGroot's implentation.
* Total number of classes are 2: one for the product and one for the backgorund class (no product). 
* For the anchor box: As mentioned in the problem statemnt only 1 anchor box per feture map is allowed. we use 6 feture maps (38, 19, 10, 5, 3, 1) as mentioned in the paper with only 1 anchor box each. Additionally the number of default boxes are: 1940 because of the 1 anchor box used for each feature map. We use a fixed ratio (width to height) for the anchor box used i.e.,"0.10:0.12". The reason is explained in **Q&A** Section.


**This is the first draft and a considerable speed increase can be achieved for a particular dataset.**

For any queries [contact](raotnameh@gmail.com).
