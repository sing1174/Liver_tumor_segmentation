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
Now open liver_segmentation.ipynb file and run it for training ResUnet with pre-processed CT scan images and their corresponding liver masks. It will generate the models folder. There are already three pre-trained models trained on 25%, 50% and 100% data in the models folder. We get following epochs.

![image](https://private-user-images.githubusercontent.com/39149911/295383009-db91138e-5797-499e-99d5-499819b70a07.jpeg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDQ4NDk4MjIsIm5iZiI6MTcwNDg0OTUyMiwicGF0aCI6Ii8zOTE0OTkxMS8yOTUzODMwMDktZGI5MTEzOGUtNTc5Ny00OTllLTk5ZDUtNDk5ODE5YjcwYTA3LmpwZWc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwMTEwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDExMFQwMTE4NDJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT03ZWRmNjZiY2ZkZmE0YzdmN2VlZGU0NWFkY2NlYmE3YWZjNmQ4ZDY1OTFkZGU5ZmUzMmIwMTliMTU2MjYxMTUwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.hPjRv_G3MvzHTd4LSmgI3cx8yPIHpKTeFryvc1timMM)

Run Liver_segmentation_results.ipynb to view the outputs. Run models in models folder or using your trained version. We see the results and evaluation metric information there.

Then run Tumor_segmentation.ipynb file for training ResUnet for with the tumor segmentation masks and segmented liver images. This gives following results:
![image](https://private-user-images.githubusercontent.com/39149911/295389035-18f12e52-0777-4252-b4cd-31f9964a8c26.jpeg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDQ4NTA5NjIsIm5iZiI6MTcwNDg1MDY2MiwicGF0aCI6Ii8zOTE0OTkxMS8yOTUzODkwMzUtMThmMTJlNTItMDc3Ny00MjUyLWI0Y2QtMzFmOTk2NGE4YzI2LmpwZWc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwMTEwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDExMFQwMTM3NDJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1mY2ZlOTA2YmM2NjM1OTg3ZmEyNDZkNzZlODBiYTkzMjNmZGNiYjkwMmNiNWU2N2FhMjNiNWVhNTdmMmMxMTcwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.roZ6JC7RUy_CGlh-ZgkX1A4K4C40sEZOsxkfPrEiTeM)

Run Tumor_segmentation_result.ipynb to view final output. You can choose any segmentation model from the 'models' folder and try running the visualization codes.

Run on 25% of the data for faster training. You may run Tumor_segmentation.ipynb on 100 epochs for more accurate results.

