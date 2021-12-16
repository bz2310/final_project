# final_project

final_project.ipynb contains all the code necessary to run the results of the experiment. As described in the slides, the experiment structure looks like this:

![image](https://user-images.githubusercontent.com/92058849/146436890-3f2eccbe-cc2a-4fbc-88df-ce26cf5c51d2.png)

The link to all the final data can be found here: https://drive.google.com/drive/u/0/folders/12fLlUOFY08Nckk2OTmCOC1ggOxSaeel3

We visualize the data and see that there's a lot of seasonality in this data. We want to predict the second column, T (deg C), which is the temperature in degrees Celsius:
![image](https://user-images.githubusercontent.com/92058849/146437293-1ce4ec78-9e5a-4c6c-88a5-85a76fce4fe9.png)

There's also huge outliers in the wind speed data, so we clean that out
![image](https://user-images.githubusercontent.com/92058849/146437368-3b4e58d4-623f-4bbd-8936-7b44c82b7197.png)

We create daily and yearly seasonality features to account for the seasonality we see in all the data:
![image](https://user-images.githubusercontent.com/92058849/146437443-4576de05-bceb-4d3f-a2b6-0888a518c708.png)

We look at the initial feature correlation and see that a few of the features are correlated amongst each other:
![image](https://user-images.githubusercontent.com/92058849/146437554-7a12a963-c0b5-4e64-9074-250ad429a70d.png)


I then created a WindowGenerator class to create sliding windows as inputs and outputs for time series prediction, as demonstrated in the slides:
![image](https://user-images.githubusercontent.com/92058849/146437684-521f65fb-1513-4bba-aa4b-b17293e1d3d4.png)

70% of the data is used for training, 20% for validation, and 10% for testing. I generate the three window types as shown by this string representation of indices:
![image](https://user-images.githubusercontent.com/92058849/146437771-a13e1d93-c80a-4ce6-815b-3e9f61114a41.png)

I have a compile and fit function that takes any DNN and gives it a timing callback, early stopping, and checkpointing:
![image](https://user-images.githubusercontent.com/92058849/146437911-4650a5f0-ca7f-41c8-a074-c7c2935f9ff8.png)

I use this to run and save data (as seen in the Google Drive) of all the experiment variations. Here's how to run experiment variations for the base model:
![image](https://user-images.githubusercontent.com/92058849/146437997-4e327654-cf5b-4398-b0e5-3bdca495fc0d.png)

And here's how to run experiment variations for the LSTM models:
![image](https://user-images.githubusercontent.com/92058849/146438037-cf289347-c981-4cbf-89d5-616ff3813d54.png)

I can then visualize what it looks like to use the past 24 hours as inputs, and compare the actual label vs the prediction for the next hour:
![image](https://user-images.githubusercontent.com/92058849/146438348-9911ee3d-626b-4466-964d-496990bf7775.png)

I can also visualize the training and validation loss over epochs for each experiment, based on the saved and checkpointed data for every single experiment:
![image](https://user-images.githubusercontent.com/92058849/146438422-b54331d9-3630-44bf-812e-460d410df6f9.png)

The next file, final_project_analysis.ipynb is to collect all the results from my Google Drive and compare the experiments to each other. It generates tables such as the ones seen in the slides:
![image](https://user-images.githubusercontent.com/92058849/146438553-9f3d99f3-775b-454b-a8f4-bb259cd26ace.png)

These are all the files and data that are needed to regenerate my slides and data. 
