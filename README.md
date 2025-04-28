# CS50AI | Lecture 4 - Learning | Project 1 - [Shopping](https://cs50.harvard.edu/ai/2024/projects/4/shopping/)

This project is a mandatory assignment from **CS50AI – Lecture 4: "Learning"**. It involves building an AI model using a **nearest-neighbor classifier** that predicts whether a user will complete a purchase on a shopping website based on their browsing behavior.

---

## 📌 Usage

To run the project locally, follow these steps:

1. Clone this repo.
2. Install the required Python libraries (you mainly need `scikit-learn`):
   ```bash
   pip install scikit-learn
   ```
3. In terminal, run:
   ```bash
   python shopping.py shopping.csv
   ```

The program will output:
- Number of correct and incorrect predictions
- True Positive Rate (Sensitivity)
- True Negative Rate (Specificity)


## Project Overview

In this project, the goal is to predict **whether a visitor will generate revenue (make a purchase)** based on their session data.  
The dataset contains various features such as:
- Number of administrative, informational, and product-related pages visited
- Time spent on those pages
- Bounce rates, exit rates, page values
- Special day proximity
- Month of visit
- Type of visitor (returning or new)
- Weekend indicator

Using this information, the model tries to learn patterns and predict if a session results in a purchase.

The chosen machine learning method is **k-Nearest Neighbors (k-NN)** with **k = 1**, meaning the model predicts based on the single most similar instance from the training data.

---

## My Task

The task for this project was to:

- Load and preprocess the shopping dataset.
- Convert categorical data (like month names and visitor type) into numerical formats.
- Split the data into training and testing sets using a 60-40 split.
- Train a k-NN classifier (k=1) on the training data.
- Make predictions on the test data.
- Evaluate the model by calculating:
  - **Sensitivity (True Positive Rate)**
  - **Specificity (True Negative Rate)**
- Report the number of correct and incorrect predictions, along with the sensitivity and specificity percentages.

---

## Implementation Explanation

Here's a high-level breakdown of how I approached and implemented the project:

- **Loading and Preprocessing Data**:
  - Used Python’s built-in `csv` module to read the data.
  - Categorical features like `Month`, `VisitorType`, and `Weekend` were mapped to numerical values:
    - `Month` converted to an index (0-11).
    - `VisitorType` set to 1 for "Returning_Visitor", 0 otherwise.
    - `Weekend` converted to 1 (True) or 0 (False).
    - The target variable `Revenue` similarly mapped to 1 (True) or 0 (False).

- **Splitting Data**:
  - Used `train_test_split` from `scikit-learn` to split the dataset into 60% training and 40% testing.

- **Training the Model**:
  - Trained a **k-Nearest Neighbors** classifier (`KNeighborsClassifier`) with `k=1`.
  - The classifier fits based on the Euclidean distance between feature vectors.

- **Evaluating the Model**:
  - Compared predicted labels against actual labels.
  - Calculated:
    - **Sensitivity** as the proportion of actual positives correctly predicted.
    - **Specificity** as the proportion of actual negatives correctly predicted.

- **Result Output**:
  - Printed the number of correct and incorrect predictions.
  - Displayed the sensitivity and specificity as percentages with two decimal precision.

