## AI, Machine Learning and Deep Learning 

- AI is the broader field of making computers perform tasks that normally require human intelligence, such as decision making, recognition and problem solving. 

- Machine Learning = subset of AI where systems learn patterns from data instead of being programmed for every situation. 
 
- Deep Learning = subset of Machine Learning that uses neural networks with multiple layers to learn complex pattern in data. 

so basically `AI ⊃ ML ⊃ DL` 


---


##  Supervised vs Unsupervised Learning

### Supervised Learning

- Here model trained using labelled data, ie we provide the model with both the input and the correct output
- The dataset contains: Features (input variables), Labels/targets (expected output)

2 of the most common supervised learning problems are:

#### Regression 
Predicting a continuous numerical value. eg a house price.

#### Classification
Predicting a category/class.

Examples: 
- spam or not 
- cat or dog
- disease or no disease


### Unsupervised Learning

In unsupervised learning, the data does not have labelled outputs.

The model attempts to discover patterns or structures within the data.

It can be applied to
- clustering (which involves grouping together similar items),
- anomaly detection (which means identifying odd values)
- dimensionality reduction (which consists of simplifying complex data).


---

##  Training, Validation and Test Sets

A dataset is commonly divided into different subsets.

### Training Set

used to train the model from which it  learns patterns and relationships.

### Validation Set

used during model development to evaluate different model choices.
helps decide which version of the model should be used.

### Test Set

used at the end to estimate how well the final model performs on unseen
data.
since its for testing, hence it should not be used to train the model. since evaluating the model on the data it was trained will not give up clear idea of how it will perform on unseen data.

### Typical workflow

Dataset
   ↓
Training data → Train model
   ↓
Validation data → Tune/select model
   ↓
Test data → Final evaluation

---


## What is a Machine Learning Model?

A model is a mathematical representation that learns a relationship or pattern from data.

### Training process

1. give the model training data.
2. model makes predictions.
3. compare predictions with actual values.
4. calculate an error/loss.
5. adjust model parameters to reduce the loss.
6. repeat this process. until the error is as small as possible.

The goal is not simply to memorize the training data, but to learn patterns that generalize to new data.

---


## Data Cleaning and Preprocessing

real-world data is messy, not suitable to train machines with 

It can contain:
- missing values
- incorrect values
- duplicate records
- outliers
- categorical values
- different scales
if this kinda data is fed to a model, twill make incorrect predictions.
data preprocessing prepares the data so that it can be used effectively by a Machine Learning model.

typical workflow:

raw data
   ↓
clean data
   ↓
handle missing values
   ↓
handle outliers
   ↓
encode categorical data
   ↓
scale features
   ↓
train model


---

## Handling Missing Data

missing data occurs when some values in a dataset are unavailable. this can be fixed by a few methods, choice of imputation strategy depends on the type, distribution of the data:
### Common approaches

#### 1. Remove rows

rows containing missing values can be removed.

useful when:
- only a small number of values are missing
- removing them will not significantly affect the dataset

#### 2. Mean Imputation

replace missing numerical values with the mean.

eg:
values:
10, 20, 30

mean = 20

missing value → 20

#### 3. Median Imputation

replace missing values with the median.

often useful when the data contains extreme values/outliers.

#### 4. Mode Imputation

for categorical data, the most frequently occurring category can be used.

eg:
male, male, female, male, MISSING

MISSING → male

---

## Handling Outliers

an outlier is a data point that is a bit too far from the other observations

eg:
heights: 170, 172, 168, 171, 169, 250

250 is likely an outlier.

### Why can outliers be a problem?

Outliers can:
- Distort statistical measures such as the mean
- Affect some ML models
- Make patterns harder to learn

methods like `IQR` can be used to identify outliers.

### What can be done?

Depending on the situation:
- Investigate the value
- Correct incorrect data
- Remove the value if it is clearly invalid
- Transform the data
- Keep it if it represents a genuine observation

**An outlier should not automatically be deleted.**


---


## 8. Categorical Encoding

machine Learning models work with numerical representations and hence are unable to carry out these mathematical operations on strings while real datasets can contain categorical values.

Example:

| size  |
| ----- |
| small |
| med   |
| Large |

these categories need to be represented numerically.

### Label Encoding

categories are assigned numerical values.

Example:

small → 0
Medium → 1
Large → 2

This can be appropriate when categories have an actual order.

### One-Hot Encoding

Each category gets its own binary column.

Example:

Size = Small / Medium / Large

| Small | Medium | Large |
| ----: | -----: | ----: |
|     1 |      0 |     0 |
|     0 |      1 |     0 |
|     0 |      0 |     1 |

one-hot encoding is useful for nominal categories where there is no natural
ordering.


---
## 10. Overfitting vs Underfitting

### Overfitting

overfitting occurs when a model learns the training data too closely, including noise or random patterns. the model performs very well on training data but poorly on unseen data.
aka model gets too accustomed to the training data.
eg:
training accuracy: 99%
test accuracy: 60%

=> model may have overfitted.

#### Ways to reduce overfitting

- use more training data
- reduce model complexity
- regularization
- cross-validation
- early stopping
- remove irrelevant features


### Underfitting

Underfitting occurs when a model is too simple to capture the underlying patterns in the data.

model performs poorly on both training and unseen data. 
aka model is just trash 
eg:
training accuracy: 60%
test accuracy: 58%

#### Ways to reduce underfitting

- Use a more complex model
- Add useful features
- Reduce excessive regularization
- Train for longer when appropriate


### Main idea

underfitting:
model is too simple → fails to learn enough.

overfitting:
model learns training data too specifically → fails to generalize.

Good model:
learns useful patterns → performs well on unseen data.
