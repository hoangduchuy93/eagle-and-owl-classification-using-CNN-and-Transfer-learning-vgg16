![image](https://user-images.githubusercontent.com/91864024/181451237-d51b1c4d-9fdd-45ef-b1c9-97e7f37909f5.png)

# Eagle and owl classification using CNN and Transfer Learning VGG16
## I. Outline
- People have always been fascinated with owls and eagles, which haven’t changed over time. Both of these are aggressive birds that are known to combat and protect their territory. 
- However, eagles are considerably more powerful and more sturdy than owls. Also, they are larger and weigh more than owls.
- This project will classify two species of eagle and owl using CNN neural network for learning purposes

## II. Business Objective/ Problem
- Assume that you work in the Data Science department of a company that specializes in providing automated solutions, including image classification systems. Your client is currently working on a poultry farm.
- They complain that their animals have been lost due to being taken by large native birds. In the area, only owls and eagles are large native species. They are sure that it can only be due to the eagle because only this species is capable of catching chickens, ducks and lambs. Moreover, owls are more profitable because they hunt mice, helping to protect crops.
- Clients want a system that emits audible and visual warnings (when the eagle appears, it will make a sound and the screen will project an image of a person to scare the bird). This will not happen if the system recognizes it as an owl.
- The Data Science team's task is to find a way to classify these two bird species, then give this model to the audio and visual engineering team for further work.

## III. Project implementation
### 1. Business Understanding
Based on the above description => identify the problem:
- Find methods to classify eagle and owl based on their physical characteristics
- Objectives/problems: build a classification model to classify these 2 species for further purpose.
- Applied method: CNN model, Transfer Learning vgg16
### 2. Data Understanding/ Acquire
- Image data of the above 2 birds are downloaded from many sources for learning purposes
- image folder: incuding 5937 images for training and 1340 for testing.
- image_small: including 200 images for training and 100 images for testing.

![image](https://user-images.githubusercontent.com/91864024/181462904-35f42152-d0b5-4df2-9250-2ae674516140.png)

### 3. Build model (CNN model)
#### 3.1. Build CNN model (without transfer learning VGG16)
**Init CNN model**

![image](https://user-images.githubusercontent.com/91864024/181463928-a6a61e7f-31a7-4f49-8010-1453a170b432.png)

**Compile CNN model**

![image](https://user-images.githubusercontent.com/91864024/181464065-a2668e5d-d827-48c6-b00e-c7e10350c46a.png)

**Desclare EarlyStopping and fit model**

![image](https://user-images.githubusercontent.com/91864024/181464185-92b36c08-72b1-4425-9469-a420c6fe8188.png)

![image](https://user-images.githubusercontent.com/91864024/181464236-4babf7f2-737e-4cab-940d-cc3b006090ef.png)

![image](https://user-images.githubusercontent.com/91864024/181464342-8bb14e79-a015-4bd0-b5e3-ad5a4e4758c5.png)

Comment: accuracy score ~ 83%

**Save model**

![image](https://user-images.githubusercontent.com/91864024/181464501-1f21369b-f579-4ba8-9fbe-7b00d700728a.png)

#### 3.2. Prediction
#### A. Predict an Eagle

![image](https://user-images.githubusercontent.com/91864024/181471335-8e6bf264-e040-4687-97b2-51920203229c.png)

![image](https://user-images.githubusercontent.com/91864024/181471463-898a0a5c-8776-4644-bc16-c0b8fa6168c7.png)

#### B. Predict an Owl
![image](https://user-images.githubusercontent.com/91864024/181471606-001ffccb-891d-4903-a27e-0f87c0b43b77.png)

![image](https://user-images.githubusercontent.com/91864024/181471658-9e44b81e-be90-4c3d-8e11-d149899e95c4.png)

#### 3.3. Conclusion
- With current model, we can classify eagles and owl.
- We can give this model to the audio and image engineer for further business. However, to make sure we can choose the best model, we will use another method (Transfer learing VGG16).
- Let's check if VGG16 have better accuracy and runtime.

![image](https://user-images.githubusercontent.com/91864024/181521734-f4b97882-7ebb-49f7-8091-76863e052305.png)

### 4. Build model with Transfer learning VGG16
- We can use the pre-trained model VGG16 to check if we can have better accuracy and runtime.
- There are 2 options for VGG16:
  - VGG16 with small dataset. Here we use 200 images for training and 100 images for testing (image_small folder)
  - VGG16 with big dataset. Here we use the same dataset for training and testing as being mentioned at section 2 (image folder)
  - We will run through these 2 options, and compare with CNN model (section 3) to choose the best model among them.

#### 4.1 Option 1: VGG16 with small dataset (image_small folder)

**- Frozen and add more layers to VGG16**

![image](https://user-images.githubusercontent.com/91864024/181520243-a1f4bc3c-de00-42e3-8a64-420131946a3b.png)

**- Init train/ test**

![image](https://user-images.githubusercontent.com/91864024/181520362-b79a94ca-3852-4904-ab2e-80dfe158ba79.png)

**- EarlyStoping**

![image](https://user-images.githubusercontent.com/91864024/181520584-e1ca5365-b0d0-44e7-959d-d43a81acabfc.png)

**- Fit model**

![image](https://user-images.githubusercontent.com/91864024/181520673-a6d6ec1e-a6a3-4dd7-85f3-346bf4df7055.png)

**- Save model VGG16 with small dataset**

![image](https://user-images.githubusercontent.com/91864024/181520753-7b2c0fec-d3d3-41f2-a407-29bd8741adb6.png)

#### 4.2 Option 2: VGG16 with big dataset (image folder)

**- Init model VGG16**

![image](https://user-images.githubusercontent.com/91864024/181522106-8a8f334d-35ab-4430-ab02-2c28adf9f668.png)

**- Frozen and add more layers to VGG16**

![image](https://user-images.githubusercontent.com/91864024/181522243-b4ce137e-7bbd-46fc-802c-91a403fc0736.png)

**- Init train/ test**

![image](https://user-images.githubusercontent.com/91864024/181522394-49ce40a0-2429-4322-8d6e-ba335b862949.png)

**- Fit model**

![image](https://user-images.githubusercontent.com/91864024/181522504-19bafb76-0f18-4674-8279-3445833c317d.png)

**- Save model VGG16 with big dataset**

![image](https://user-images.githubusercontent.com/91864024/181522614-9e498a7f-68a4-4cab-82a1-607ef4cfeee2.png)

![image](https://user-images.githubusercontent.com/91864024/181524195-ec19dd34-d1d9-4c11-be6a-451b9f9a7ceb.png)

### 5. Conclusion
With 3 models (using self-built CNN model, vgg16 with small dataset, vgg16 with big dataset), we have the following comments:
- Self-built CNN model: time ~ 53 minutes, accuracy ~ 83%
- Vgg16 with small dataset: time ~ 7 minutes, accuracy ~ 70%
- Vgg16 with big dataset: time ~ 1h28p, accuracy ~ 52%

-> use self-build CNN model for better results and time.

Thank you for your experience with my project. Hope you enjoy it!

























