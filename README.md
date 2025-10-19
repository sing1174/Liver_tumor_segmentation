# Liver_tumor_segmentation
Using ResUnet to segment liver tumors from CT scan images. Refer to this [report](https://github.com/1998anwesha/Liver_tumor_segmentation/blob/main/Liver_tumor_segmentation_using_ResUNet.pdf) for details regarding methodology, loss metrics, results and future work.

We have used Google Colab pro for this project. The training code can also work on normal Colab using T4 GPU and memory space of less than 30 GB. 

## File and dataset extraction
First, extract the file content onto one folder "imageprocessing" in google drive "MyDrive". Now, this folder should have multiple folders and Colab files  
Download dataset Liver segmentation [3D-IRCADb-01](https://www.ircad.fr/research/data-sets/liver-segmentation-3d-ircadb-01/).  This is a zip file of size 806 MB.
Create a new folder called "Dataset" in "imageprocessing" and place this zip file there.

Next, open dataset_generation.ipynb in Google Colab. Follow the instructions in it. 
On running this, "train" folder will be created in “imageprocessing”. Total time taken for data extraction will be around 2 hours.

## Training Liver and Tumor segmentation models
Now open liver_segmentation.ipynb file and run it for training ResUnet with pre-processed CT scan images and their corresponding liver masks. It will generate the models folder. There are already three pre-trained models trained on 25%, 50% and 100% data in the models folder. We get the following epochs.

| **Epoch** | **Loss** | **Accuracy** | **Dice Coefficient** | **Val Loss** | **Val Accuracy** | **Val Dice Coefficient** |
| :-------: | :------: | :----------: | :------------------: | :----------: | :--------------: | :----------------------: |
|     1     |  0.1457  |    0.9492    |        0.8569        |    0.9785    |      0.9031      |          0.0215          |
|     2     |  0.1226  |    0.9538    |        0.8773        |    0.9231    |      0.9094      |          0.0769          |
|    ...    |    ...   |      ...     |          ...         |      ...     |        ...       |            ...           |
|     13    |  0.0908  |    0.9566    |        0.9092        |    0.1271    |      0.9543      |          0.8729          |
|     14    |  0.0907  |    0.9569    |        0.9093        |    0.1119    |      0.9555      |          0.8881          |
|     15    |  0.0849  |    0.9577    |        0.9151        |    0.3062    |      0.9405      |          0.6938          |




Run Liver_segmentation_results.ipynb to view the outputs. Run models in models folder or using your trained version. We see the results and evaluation metric information there.

Then run Tumor_segmentation.ipynb file for training ResUnet for with the tumor segmentation masks and segmented liver images. This gives the following results:
| **Epoch** | **Loss** | **Accuracy** | **Dice Coefficient** | **Val Loss** | **Val Accuracy** | **Val Dice Coefficient** |
| :-------: | :------: | :----------: | :------------------: | :----------: | :--------------: | :----------------------: |
|     1     |  0.6114  |    0.9795    |        0.3977        |    0.8145    |      0.9328      |          0.1855          |
|     2     |  0.4629  |    0.9928    |        0.5361        |    0.7656    |      0.9513      |          0.2344          |
|    ...    |    ...   |      ...     |          ...         |      ...     |        ...       |            ...           |
|     28    |  0.4518  |    0.9946    |        0.5482        |    0.4034    |      0.9954      |          0.5966          |
|     29    |  0.4004  |    0.9950    |        0.5996        |    0.4399    |      0.9945      |          0.5601          |
|     30    |  0.3707  |    0.9956    |        0.6293        |    0.4633    |      0.9954      |          0.5367          |


Run Tumor_segmentation_result.ipynb to view final output. You can choose any segmentation model from the 'models' folder and try running the visualization codes.

Run on 25% of the data for faster training. You may run Tumor_segmentation.ipynb on 100 epochs for more accurate results.

