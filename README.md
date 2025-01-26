# Mnist
Step1:
Firstly, we downloaded the minist data from https://www.kaggle.com/ . Before we start we checked our dataset if it included any null values and Elhamdollah there wasn’t any null values . After that we split our dataset x which is the feature and y is our label to 20 percent validation and 80 percent training . Then we set our batch size and used dataloader to split the training and validation sets into batches . We checked if our device has a gpu and if it has it we will use it in further computations which will make much faster and easier . 

![image](https://github.com/user-attachments/assets/ad49be86-f4ff-4b7d-8b9a-ad7bc190f873)

Step2:
Secondly, we created our model by 3 layers (2 hidden layers and one output). We take our picture with a shape of 28*28 which equals to 784 which will be the number of features in our input layer . every hidden layer consists of 150 unit and linear function and a non linear activation(for non-linearity) function and we will choose relu in our case  . The output layer consists of 10 units (The numbers between 0 and 9) and linear function and a non linear activation(for non-linearity) function and we will choose softmax to give us the probability of each number and it will take the maximum probability which will be our predict . 

![image](https://github.com/user-attachments/assets/0f16cfa0-cb10-4bcd-af84-a29f7334e797) ![image](https://github.com/user-attachments/assets/e372030d-adea-481a-ac90-3de91a8d6f51)

Our Model Architecture 

![image](https://github.com/user-attachments/assets/fec6cebb-3b97-4b23-836d-1971edac0a83)

As given, We will use Cross Entropy Loss function(hint!! In our implementation in the code we will not use softmax as the cross entropy already use it before calculating the loss). We set the learning rate to 0.01. We will use Adam optimizer to minimize our loss function.

We will train our model for 10 epochs and each epoch consists of 375 Iteration . 
We will calculate the accuracy and loss every 75 Iteration which means 5 times per epoch for training and validation . We will print the loss and accuracy for the training and validation in every 250 Iteration. We reached 90 percent accuracy for the training and validation .
Now we will show our model performance on minsit data:

![image](https://github.com/user-attachments/assets/999d9fca-8f8e-4064-b8f9-7c0e9c2723fe)

Now will show the plots:
1-performace on training:

![image](https://github.com/user-attachments/assets/0d4781b1-0f8a-4005-a939-c73aebe772d4) ![image](https://github.com/user-attachments/assets/00ecdb8b-6dbf-4a03-917c-cb9bf30e84af)

2-performace on validation:

![image](https://github.com/user-attachments/assets/bd45bd1c-fc3d-4e1a-8be0-ada311b6b584) ![image](https://github.com/user-attachments/assets/86097d38-46ed-40ad-8a08-7fbed9b4387b)


Step 3 
Now we will add layer normalization and dropout to our model . Layer normalization enables smoother gradients, faster training, and better generalization accuracy. And dropout prevents overfitting. We will see later it will increase the accuracy of our model and decrease the loss.
After some trails we get the best performance when we use layer normalization after each hidden layer and use one dropout layer after the 2nd hidden layer but off course we put the dropout layer before the normalization layer so we make less computations(Hint!! We used the default probability of dropout which is 0.5)
Our model performance:

![image](https://github.com/user-attachments/assets/617a3bcc-eaf3-45ad-9bde-1d1a022aa7e6)

Now with the plots:
1-performance on training

![image](https://github.com/user-attachments/assets/573b29a5-0875-4646-85e8-b5ce08558bec) ![image](https://github.com/user-attachments/assets/3d377015-59d9-449e-b355-c1c865511334)

2-performance on validation :

![image](https://github.com/user-attachments/assets/4e246998-346c-400a-b6b8-31250fb08c92) ![image](https://github.com/user-attachments/assets/4fd82c88-985b-4d38-aa04-b5d5c8fe604f)


From the plots we can see that the accuracy of our model increased  and the model become more generalization because we added the normalization and dropout  layer as we said that previously.
Step 4
Now we will compare between  different learning parameters and the probability of the dropout layer .
1-	Learning rate= 0.001 and probability = 0.2

![image](https://github.com/user-attachments/assets/d78aef82-7a5a-4dce-9da3-da0866752a57)


And the plots:

![image](https://github.com/user-attachments/assets/1113b7e3-d2bb-46ec-b619-015e50c2a8f6) ![image](https://github.com/user-attachments/assets/bddfbf7c-7e54-4642-8c2f-58482a09054b)

![image](https://github.com/user-attachments/assets/ee446aa1-9ffb-428b-892e-139b23889c92) ![image](https://github.com/user-attachments/assets/b2002152-9509-486b-bd61-7ff1eb7a0cb7)

We can se that this hyperparameter are much better because it make our model have better performance and better accuracy on the training and validation set and also it make our model faster to find the min of our activation function and the probability of dropout will make a 20 percent of our unit to be zeroed  
2- Learning rate= 0.0005 and probability = 0.4

![image](https://github.com/user-attachments/assets/677e868c-f43a-491d-8baa-ad23dcb6e771)


The plots:

![image](https://github.com/user-attachments/assets/5fcf95a2-3993-42fb-bf4e-3de8debad304) ![image](https://github.com/user-attachments/assets/2c5da905-0769-46f0-b641-0f3bae36d3c1)

![image](https://github.com/user-attachments/assets/bfe1e70d-ddf9-46d5-8135-998798469f54) ![image](https://github.com/user-attachments/assets/fc780507-ec99-4803-b278-28d45619f426)

We can see that the model is a little slower in the start than previous hyperparameters to find the best solution but at the end it will have nearly the same accuracy and the probability of dropout will make a 40 percent of our unit to be zeroed  

3-learning rate=0.0001 and probability = 0.6

![image](https://github.com/user-attachments/assets/5a5cad59-fac8-49c7-885c-5add50ef3e0a)

The plots:

![image](https://github.com/user-attachments/assets/208d0f6f-9db0-4187-b343-e67d8520c646) ![image](https://github.com/user-attachments/assets/e34968e5-7632-4888-9c89-564e190bc311)

![image](https://github.com/user-attachments/assets/f46e1e7d-f459-4ca0-abe2-6d63416249ab) ![image](https://github.com/user-attachments/assets/5d036791-c1ff-4bb6-b01e-0f8ef4159560)

Now with these hyperparameter the learning rate is to small which will make our model much slower to find its goal  but at the end it will reach the goal anyway and the probability of dropout will make a 60 percent of our unit to be zeroed  







