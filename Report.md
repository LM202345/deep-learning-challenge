## 1.Overview of the analysis: Explain the purpose of this analysis.

The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures.

From Alphabet Soup’s business team, you have received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as:
* EIN and NAME—Identification columns
* APPLICATION_TYPE—Alphabet Soup application type
* AFFILIATION—Affiliated sector of industry
* CLASSIFICATION—Government organization classification
* USE_CASE—Use case for funding
* ORGANIZATION—Organization type
* STATUS—Active status
* INCOME_AMT—Income classification
* SPECIAL_CONSIDERATIONS—Special considerations for application
* ASK_AMT—Funding amount requested
* IS_SUCCESSFUL—Was the money used effectively



## 2.Results: Using bulleted lists and images to support your answers, address the following questions:
### Data Preprocessing

* What variable(s) are the target(s) for your model?
The variable target is the column IS_SUCCESSFUL because since it could indicate whether the money was used effectively in an application request or not.

* What variable(s) are the features for your model?

    * APPLICATION_TYPE—Alphabet Soup application type
    * AFFILIATION—Affiliated sector of industry
    * CLASSIFICATION—Government organization classification
    * USE_CASE—Use case for funding
    * ORGANIZATION—Organization type
    * STATUS—Active status
    * INCOME_AMT—Income classification
    * SPECIAL_CONSIDERATIONS—Special considerations for application
    * ASK_AMT—Funding amount requested


* What variable(s) should be removed from the input data because they are neither targets nor features?

EIN and NAME—Identification columns

### Compiling, Training, and Evaluating the Model

* How many neurons, layers, and activation functions did you select for your neural network model, and why?

 First hidden layer
nn.add(tf.keras.layers.Dense(units=80, activation="relu",input_dim=43))

  Second hidden layer
nn.add(tf.keras.layers.Dense(units=30, activation="relu"))

 Output layer
nn.add(tf.keras.layers.Dense(units=1, activation="sigmoid"))


 First hidden layer
nn.add(tf.keras.layers.Dense(units=100, activation="relu",input_dim=37))

 Second hidden layer
nn.add(tf.keras.layers.Dense(units=50, activation="relu"))

 Capa de dropout
nn.add(tf.keras.layers.Dropout(0.3))  # Add dropout for regularization

 Third hidden layer
nn.add(tf.keras.layers.Dense(units=20, activation="relu"))  # Increase units

# Output layer
nn.add(tf.keras.layers.Dense(units=1, activation="sigmoid"))

I selected 100 neurons in the first layer to allow the model to learn intricate features in the data, and I chose 50 neurons in the second layer to maintain a balance between model complexity and generalization.

I added three hidden layers to the network to capture increasingly abstract representations of the data, which can help improve the model's performance.
I used ReLU activation functions in the hidden layers to introduce non-linearity, allowing the model to learn complex relationships within the data. For the output layer, I used a sigmoid activation function as it's suitable for binary classification problems like this.


* Were you able to achieve the target model performance?
 No

* What steps did you take in your attempts to increase model performance?

* Increase the number of First hidden layers, decrease the number of Second hidden layer, increase the number of the epochs
* Increase the complexity of the network by adding more units to the hidden layers (e.g., 100 units in the first layer and 50 units in the second layer).
* Add a dropout layer with a rate of 0.3 to help prevent overfitting.
* Add a third hidden layer.
* Increase the number of training epochs to 200 to give the model more time to converge.
* Increase the batch size to 32, which can speed up the training process.


## Summary: Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and then explain your recommendation.
Model: "sequential"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 dense (Dense)               (None, 80)                3520      
                                                                 
 dense_1 (Dense)             (None, 30)                2430      
                                                                 
 dense_2 (Dense)             (None, 1)                 31        
                                                                 
=================================================================
Total params: 5,981
Trainable params: 5,981
Non-trainable params: 0

268/268 - 0s - loss: 0.5620 - accuracy: 0.7291 - 289ms/epoch - 1ms/step
Loss: 0.5620246529579163, Accuracy: 0.7290962338447571

Model: "sequential_5"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 dense_18 (Dense)            (None, 100)               3800      
                                                                 
 dense_19 (Dense)            (None, 50)                5050      
                                                                 
 dropout_1 (Dropout)         (None, 50)                0         
                                                                 
 dense_20 (Dense)            (None, 20)                1020      
                                                                 
 dense_21 (Dense)            (None, 1)                 21        
                                                                 
=================================================================
Total params: 9,891
Trainable params: 9,891
Non-trainable params: 0

204/204 - 0s - loss: 0.6930 - accuracy: 0.7367 - 204ms/epoch - 1ms/step
Loss: 0.6930334568023682, Accuracy: 0.7366645932197571

Recommendation: I recommend using a Random Forest classifier for this classification problem, Random Forest can handle a variety of data types and feature  effectively, making it a strong choice for classification tasks.