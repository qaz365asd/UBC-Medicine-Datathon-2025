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

## 1. Setting up Google Colab:
- Visit: [https://colab.research.google.com/](https://colab.research.google.com/)
- Sign in with your Google account.
- Select **File > New notebook** in Drive.

![image](https://github.com/user-attachments/assets/933f35ab-35cc-4bcb-9e40-cd28d728bbc3)

---

## 2. For NIH Chest X-ray and Stroke Prediction Datasets Only:
- Download the dataset from Kaggle as a **ZIP** file.

![image](https://github.com/user-attachments/assets/04bf342e-2af3-4a83-999f-a880e453476c)

- Extract the ZIP file locally.

---

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

- You are now ready for exploratory data analysis and further data processing!


