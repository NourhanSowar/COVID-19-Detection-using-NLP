# COVID-19-Detection-using-NLP

Presentation Link:
https://www.youtube.com/watch?v=uSDq2PNSypE 


In this blog, we have focused in distinguish the cough to determine if the person is infected with coronavirus or not.



## We start by importing the packages and configuring some settings.
![image](https://user-images.githubusercontent.com/48545560/136244898-567e541f-3817-4cb7-b872-07999c8ee9a8.png)



## Loading Data 

We read the data set coughvid from the virufy repo.

![image](https://user-images.githubusercontent.com/48545560/136244969-66efaa00-68b8-4906-86e4-911cba617c76.png)


It contains a CSV file that contains the patient ids and some information about the patient health.

![image](https://user-images.githubusercontent.com/48545560/136245058-0b829ccd-26ab-432e-8964-b285126eb460.png)

Visualizing dataset


![image](https://user-images.githubusercontent.com/48545560/136245110-0726f080-6891-48c9-8cc2-acb026f4c734.png)


## Audio Preprocessing


Using the trim method from libsora library, we have implemented the trim_silence function to trim silence from the audio signal and its intervals.
![image](https://user-images.githubusercontent.com/48545560/136245213-68cda46c-79a4-47bb-8897-32224f791291.png)


Get mel spectrogram using libsora method and convert it to DB and save the result as image .png.

![image](https://user-images.githubusercontent.com/48545560/136245259-ebf5f332-b15d-4015-bb35-6e793b3a8e2f.png)



Get raw MFCC feature and get the label of every patient.

![image](https://user-images.githubusercontent.com/48545560/136245292-74745e3c-e5d2-4718-9f59-24be8c5ed01c.png)




Then implement and filter data set to extract necessary features in JSON files.


![image](https://user-images.githubusercontent.com/48545560/136245332-9079b318-5b48-4a6a-962a-5f487aae7f43.png)



The JSON file contains a dictionary of dictionary patient ID, mel spectrum image. MFCC coefficients, and labels.

![image](https://user-images.githubusercontent.com/48545560/136245397-c621bb23-1984-458a-9da2-a0f886fb810a.png)









## Approach 1 using MFCC Coff and labels:

Work on JSON files and create a CSV file contains only patient ID, rawMFCC, and labels.

![image](https://user-images.githubusercontent.com/48545560/136245459-b8cfa17a-20ec-4e29-bbff-d3f11397ee06.png)

## - Model Architecture:
 
Implement logistic regression architecture:
![image](https://user-images.githubusercontent.com/48545560/136245546-9cbeb505-2e05-4ea7-9d61-611a95d8367c.png)


And the result is :

![image](https://user-images.githubusercontent.com/48545560/136245599-000fadec-ab79-4bc0-81f0-ca558d75de27.png)







## Approach 2:

In this approach, we have worked on images generated from mel scale and labels



## -Preprocessing to extract images and their labels:




![image](https://user-images.githubusercontent.com/48545560/136245652-e548b9de-9236-4a63-8769-fe3609a9bf50.png)


















Using ImageGenerator to overcome unbalanced data:

![image](https://user-images.githubusercontent.com/48545560/136245732-038010ac-4cf4-415e-81a1-41b46ddbde9b.png)







Then, Implement a CNN model 
![image](https://user-images.githubusercontent.com/48545560/136245816-a6de787d-fc78-40f8-850f-9ed1ba549c9e.png)

 Using Mobilenet architecture and adam optimization
![image](https://user-images.githubusercontent.com/48545560/136245853-595ceee2-e802-4ffa-86f8-66676e2f8935.png)

The result is :

![image](https://user-images.githubusercontent.com/48545560/136245902-f93f35d1-6173-4236-8706-3d5110190e08.png)


Then using Resnet 50 and use 20 epochs to train :

![image](https://user-images.githubusercontent.com/48545560/136246013-50f3454b-b1e8-4e60-b169-52a6169f2200.png)


Getting the result :

![image](https://user-images.githubusercontent.com/48545560/136246050-cb1a9b7e-0b3c-458d-a55a-88e9c50bc56c.png)



