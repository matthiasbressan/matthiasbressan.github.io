## Predicting chl a content 

In this project we want to calculate the *chlorophyll a* content (and therefore the phytoplancton) of the water column using abiotic factors.

This could be of interest as it means that one can predict pyhtoplancton concentration without the need of a photometer, potentially making it more cost effective. Disclaimer: as the dataset used is not openly available and the model might become part of a pubblication, I cant show any data here. 

## Dataset and preprocessing

The dataset used was created by Geomar (Kiel) using data measured at Boknis Eck, Eckenförde. Measurements of temperature, salinity, O2, various nutrients and *chlorophyll a* have been ongoing since 1957. more details on the dataset can be found in the following pubblication: 
* Lennartz, Sinikka T; Lehmann, Andreas; Herrford, Josefine; Malien, Frank; Hansen, Hans Peter; Biester, Harald; Bange, Hermann Werner (2014): Long-term trends at the Boknis Eck time series station (Baltic Sea), 1957–2013: does climate change counteract the decline in eutrophication? Biogeosciences, 11(22), 6323-6339, https://doi.org/10.5194/bg-11-6323-2014 

After some initial data exploration, the dataset wwas prepared for the training. As some of the parameters were not measured non-stop, we cleaned the dataset from any row containing NaN, as well as columns containing unneeded parameters. The date was transformed to a week format (in heinsight, a sinewave encoding of the date might have been a better choice). Depth and chl a were grouped into different continuous categories and one-hot encoded. 
The last step was data normalization, were we opted for a min max normalisation. Again, in heinsight a normalisation around the mean could have been the better choice as it is less susceptible for outliers. 

## NN architecture, training and results

After testing various architectures, we opted for a dense neuronal network with three layers (128, 8 and 1 neurons) and a dropout of 0.2. Training was stopped when loss and validation loss converged. The predicted values (after denormalization) from the test set can be seen below. Red dots are the predicted values, black dots the actual values. 

<img src="images/misc/chl_results.png?raw=true"/>
