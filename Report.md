# Sprint Project 05
Hardest one so far from the boot camp
Many new tools, new libraries, a lot of theory. But the most interesting one for sure.
## 1. Install
Having my own GPU I started everything locally. Everythin loaded fine in the beggining but when started to train models the problems started. I will elaborate more on this in another section. I code in my laptop but the GPU is in my desktop computer so in order to transfer code (and also for BU porpouses) I used githhub and started to get used to it. 

### Run Unit test
After completing all the required code all test pass.

test_data_augpy ..                     [ 33%]
test_detectionpy .                     [ 50%]
test_resnet_50py ..                    [ 83%]
test_utilspy .                         [100%]

### 2. Prepare your data
I managed to get the cars images and arder it as required in the csv file

### 3. Train your first CNN (Resnet50)
I started with the default configuration not having good results. Trying different parameters (dropout, learning rate, data_aug layers values, epochs, batch size) at random at first I was not getting good results. 

After evaluating my results with some fellows it was clear that the values I was using for learning rate was very high, so I would get maybe 27% of val_accuracy in just 10 epochs, but then it started go up and down for the rest of the training. I understand that it started bouncinng not finding a good minimum for the loss function. The first learning rate used was 0.001. With that I woldn't get more that 

val_accuracy=25%
val_loss=3.45

Note: 20 epochs was more than enough because it was already oscilating. 

After a couple of of test runs I found an optimal learning rate of 0.0002. This way the val_loss and val_accuracy improved much slower but it was way more consistent. With his learning rate I got:

val_accuracy=32%
val_loss=2.95

Note: Here I noticed that I needed more epochs. I started to set to 100 finding the best model between epoch 50 and epoch 80. Due to this I implemented the early stopping callback also.

In the experiments I started noticing now that the difference between train and validation was high. I used a dropout rate of 0.1. I started to try different values, being the best 0.25. This way the difference between tran and val diminished, lowering the train accuracy and improving the val_accuracy

Note: At this point I was having many errors with my GPU. I troubleshooted it but with no luck. At this point I beleive that maybe some deffective or insufficient hardware in my desktop is the reason. I couldn't make make many experiments because 2 out of 3 experiments restarted the pc. I could only complete 12 locally. And also was imposible to test a full model training because it always failed

### 4. Evaluate your trained model
The results can be found in the Model Evaluation notebook. Can't understand why the classification report doesn't work as expected because the data pass all the tests in the rpevious cell

### 5. Improve classification by removing noisy background

I leave a couple of cropped images with my code in data. I was not able to test this. It failed all the time. Like I was trying to learn how to use my local GPU when I tried the amazon servers it was very crowded. 

### 6. Final thoughts

I would have liked to be able to test the backgorund detection with a full trained model and I can't give figures of loss and accuracy. But at this point I don't think I would learn anything new after all the test I did. The code is complete, it passes all the test, I could complile and train and improve a model and managed to remove the background and get predictions from the model I trained. 