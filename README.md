# deep-learning-challenge

### Overview
This repo contains machine learning analysis done on data from the nonprofit foundation Alphabet Soup, to evaluate lending applicants whether they will be successful from the funding given by Alphebet Soup. It contains more than 34,000 organizations alongside list of features of each organization. 

### Results
**Data Preprocessing**
Data preprocessing was conducted on the dataset before implementing the neural network model.
The target variable was the column 'IS_SUCCESSFUL' which labels successful lending transactions with a 1, and a 0 when the lending money was not used effectively.
The list of feature variables used are:
APPLICATION_TYPE — Alphabet Soup application type
AFFILIATION — Affiliated sector of industry
CLASSIFICATION — Government organisation classification
USE_CASE — Use case for funding
ORGANIZATION — Organisation type
STATUS — Active status
INCOME_AMT — Income classification
SPECIAL_CONSIDERATIONS — Special considerations for application
ASK_AMT — Funding amount requested

Feature variables such as APPLICATION_TYPE and CLASSIFICATION contained extremely large number of unique types and classifications that outliers were binned and grouped under a heading 'OTHER' to improve accuracy and reduce noise.
Other data columns such as EIN and NAME were initially dropped as they were not considered to add additional information that is already provided by other features.

**Compiling, Training, and Evaluating the Model**
After preprocessing the data, scaling and plitting into training and test sets, neural network models were created and evaluated by loss and accuracy.

The first neural network model comprised of 3 hidden layers with 80, 30 and 30 nodes respectively alongside relu and sigmoid activation functions. The results of this neural network model are:
Loss: 0.5554747581481934, Accuracy: 0.7241982221603394

In order to achieve a target accuracy of 75%, further models were tested:

The second model was attempted to be created using auto-optimisation techniques using keras-tuner. With a given range of hidden layers from 1 to 6, choices of activation functions are relu, tanh and sigmoid, as well as a range of nodes of 1 to 100 for each layer, the model unfortunately ran for 3 hours with the highest accuracy achieved of 73% before the notebook shutting down due to lack of memory.

The third model tested was manually doubling the number of nodes at each layer to 160, 60 and 60. The results achieved are:
Loss: 0.5616635680198669, Accuracy: 0.7253644466400146
An increase of only 0.001 in accuracy.

The fourth model tested was to double the number of hidden layers on top of the doubling of nodes. So now the model has 6 hidden layers, with 160 nodes in the first and 60 in the 2nd to 6th hidden layer. The results are:
Loss: 0.558544397354126, Accuracy: 0.7259474992752075
These results are extremely similar to the previous test results, leading to an understanding that greater accuracy is not restricted by the power of the model but by the dataset itself.

The fifth model tested the previous understanding by dropping more columns (status, income_amt and special considerations) with the aim to reduce possible noise from too much data. The results are:
Loss: 0.555586576461792, Accuracy: 0.7290962338447571
After dropping more columns, the accuracy increased by 0.004 but however is still not achieving the accuracy of 75%.

The last model tested the opposite hypothesis, that there was not enough data to accuractely construct the model, so the NAME column was added back into the dataset and outlier names were binned to reduce noise. The results from this model are:
Loss: 0.5171756148338318, Accuracy: 0.7498542070388794

### Summary
In Conclusion using keras sequential modelling, an accuracy of 74.99% was achieved in correctly classifying whether lending money was used effectively by various organizations. There was limitations from the dataset and additional features will aid in improving the accuracy of the model further, alongisde using models such as Functional rather than sequential that provide more flexibility to connect to more layers. 
