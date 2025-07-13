<h1>Feature Extraction from GIS images</h1>

This repository attempts to extract semantic information / features from GIS images. 


### **Problem statement analysis and proposed solution**


### EDA

* The contains 3 high resolution images of sub-urban landscapes.
* The images have identifyable features like
    * **Roads** (Many are occluded due to presence of trees)
        - Muddy roads
        - Thar roads
    * **Buildings**
    * **Trees**
    * **Barren lands**
        - empty grounds
        - harvested agricutural fields in one case.
    * **Water bodies**
        - Pond/ Lakes
        - Ocean

*We limited our study to building  and roads.*



### Search for Existing solutions:

* We explored two github projects for existing  possible pretrained models. None of them provided any reliable models. 

    * <a href = "https://github.com/parshwa1999/Map-Segmentation">Repo 1</a>
    * <a href = "https://github.com/Neilblaze/Map-Path-Segmentation">Repo 2 </a>

* **Kaggle** - We found training scripts to train segmentation model for building & training. 

### Training our own segmentation

* With the training script we train two segmentation models  one for buildings and another for roads. 
* The same model can be extended to detect more objects like water bodies, barren lands,  vehicles  given sufficient data. 

* The model were trained for limited epochs, due to gpu contraints however this was sufficient for the road model to catch on however the models achieved reasonable levels on performence.

### Results:

* The road model is able to identify thar roads as the massachussets data shows, and identifies the roads only  that are gray in appearance and misses the muddy ones.

* We can trick the model into identifying the muddy 

* 

* We finally present an overlay in the results notebook

### The way ahead
* To Identify more features we need to put in effort in data collection, by  searching for more existing datasets and adapting them  to our problem , or by manual labelling. 

* We could use the pseudo label from these to extend our datasets.

* To classify terrains:
    * We could set heuristics like percentage of builing and roads cover to identify urban and sub urban space. Or percentage of forest cover to idenfy jungles. 

    * Finetune explicit U-net models for this purpose. 

## Repository structure

The respository contains the following:

**Directories**

* **Models** - Model checkpoint of the trained segmentation models.


* **Data** - TIFF files provided with the assessment


**Training scripts**
* EDA.ipynb - 
* *U_Net_Massachusetts_road_Segmentation.ipynb* - Road segmentation training script


* *U_Net_Massachusetts_Building_Segmentation.ipynb* - Building segmentation training script


**Results**
* results.ipynb - We load the trained model and use them to extract segmentation maps for buildings and roads. we process the images in small pieces and use them to produce an overlay on the entire image.
