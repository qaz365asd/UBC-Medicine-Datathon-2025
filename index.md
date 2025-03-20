---
title: Home
layout: home
---

## Datasets

The UBC Medicine Datathon 2025 provides three datasets:

- Lung CT Segmentation: https://portal.imaging.datacommons.cancer.gov/explore/filters/?analysis_results_id=TotalSegmentator-CT-Segmentations
- NIH Chest X-rays: https://www.kaggle.com/datasets/nih-chest-xrays/data/data
- Stroke Prediction Dataset: https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset/data

We encourage you to use the provided datasets. However, if you choose to use your own dataset, please note that mentors may not be able to assist you if you encounter difficulties.

# Data Processing with Google Colab

## Setting up Google Colab:
- Visit: [https://colab.research.google.com/](https://colab.research.google.com/)
- Sign in with your Google account.
- Select **File > New notebook** in Drive.

![image](https://github.com/user-attachments/assets/933f35ab-35cc-4bcb-9e40-cd28d728bbc3)

---

# Getting started with Stroke Prediction datasets (Easy):
- Download the dataset from Kaggle as a **ZIP** file.

![image](https://github.com/user-attachments/assets/04bf342e-2af3-4a83-999f-a880e453476c)

- Extract the ZIP file locally.

### In your Colab notebook, follow these steps:

#### First code cell:
```python
# Import pandas for data manipulation
import pandas as pd
# Import the file upload module for Colab
from google.colab import files
# Import io to handle file input/output
import io

# Upload the CSV file
uploaded = files.upload()
```
```python
# Replace with the actual file name you uploaded
df = pd.read_csv('healthcare-dataset-stroke-data.csv')

# Display the first few rows of the dataframe
df.head()
```
- Run the code and select the CSV file to upload when prompted.
- The dataframe should now display in the output cell.
- The uploaded file will also appear in the left sidebar under "Files."
![image](https://github.com/user-attachments/assets/ea5ec898-0bc6-4e51-b6d9-9110251fdba7)

---

# Getting Started with the NIH Chest X-ray Dataset (Intermediate)

The NIH Chest X-ray dataset is large (42 GB), so we will use **Kaggle API** and **Google Colab** to download it efficiently.

## Step 1: Get Your Kaggle API Token

1. Go to [Kaggle Account Settings](https://www.kaggle.com/settings/account) and log in or create an account.
2. Scroll down to the **API** section.
3. Click **Create New API Token**.
4. A file called **kaggle.json** will be downloaded – this contains your API credentials.

![image](https://github.com/user-attachments/assets/09b56952-9ad3-4d74-bce5-5b7e13879e81)



## Step 2: Set Up Colab to Use Kaggle API

First, let's change the runtime to TPU so we have more disk space.
![image](https://github.com/user-attachments/assets/dc76ec12-25ba-4539-82d3-f9109becadbf)
Click save.

Note that because we are using more resources, the free tier only offers about 2 hours of data processing before you have to restart the runtime and rerun all your code again.
It may be annoying, but it's free so can't complain!

### Code Cell 1: Install Libraries & Upload API Token
```python
# Install necessary libraries
!pip install kaggle
!pip install kagglehub

# Upload the kaggle.json file
from google.colab import files
uploaded = files.upload()

# Move kaggle.json to the correct directory
!mkdir -p ~/.kaggle/
!mv kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json

print("Kaggle API key configured successfully.")
```
After running this cell, upload your kaggle.json when prompted.

### Code Cell 2: Download the Dataset
```python
import kagglehub

# Download the NIH Chest X-ray dataset via KaggleHub
dataset_path = kagglehub.dataset_download("nih-chest-xrays/data")

print("Dataset downloaded successfully.")
print("Path to dataset files:", dataset_path)
```

![image](https://github.com/user-attachments/assets/a2f05524-b964-40cd-bb2c-3a358bc9629a)


### Notes:
The dataset is large, so downloading may take some time depending on your internet connection (took me around 10 mintues to download and extract).

### Reference:
For more details on accessing Kaggle datasets via API, refer to this Kaggle API tutorial notebook: https://colab.research.google.com/github/corrieann/kaggle/blob/master/kaggle_api_in_colab.ipynb

---

# Getting Started with Lung Cancer CT Dataset (Advanced)

**Note:** This dataset requires familiarity with computational tools and workflows.

## Step 1: Select Images on IDC Portal

1. Go to the IDC portal and select the CT images you want to download.

   ![Selecting Images](https://github.com/user-attachments/assets/c4f2b5ad-8b6f-47bf-a153-33bc5a1fb9e6)

2. Scroll to the top and click **Download Image** to obtain the required manifest file.

   ![Download Manifest](https://github.com/user-attachments/assets/724ffc12-88f4-44fd-9e75-5cf89e60fc14)

## Step 2: Prepare Your Environment

### Code Cell 1: Install Required Tools & Upload Manifest File

```python
# Install IDC Index CLI tool
!pip install --upgrade idc-index

# Upload the manifest file (file_manifest_aws.s5cmd) from your local system
from google.colab import files
uploaded = files.upload()
```

### Code Cell 2: Download the manifest file using idc
```python
!idc download file_manifest_aws.s5cmd 
```

You can now start exploring and analyzing the Lung Cancer CT dataset.
For additional information and tutorials, refer to the official IDC documentation: https://learn.canceridc.dev/getting-started-with-idc
