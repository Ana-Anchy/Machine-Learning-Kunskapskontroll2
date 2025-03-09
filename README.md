# ⚙️ Machine-Learning-2 – MNIST Handwritten Digit Recognition

## 🔎 Overview
This project demonstrates a complete machine learning workflow for classifying handwritten digits using the MNIST dataset. I compare **four** different models—**Random Forest**, **Extra Trees**, **Support Vector Machine (SVM)** with an RBF kernel, and **Linear SVC**—to determine which approach balances accuracy, robustness, and computational efficiency most effectively. Additionally, a **Streamlit** application is provided for real-time digit prediction, where users can draw digits directly in their browser.

---

## 🏗️ Project Workflow

1. **🔬 Exploratory Data Analysis (EDA)**
   - Loaded the MNIST dataset from `fetch_openml('mnist_784')`.
   - Inspected dataset size (70,000 images) and the distribution of digit classes (0–9).
   - Visualized sample images to confirm data integrity.

2. **🧹 Data Preprocessing**
   - Split the dataset into:
     - **Training set** 
     - **Validation set** 
     - **Test set** 
   - Applied `StandardScaler` to normalize pixel intensities, ensuring improved model performance and training stability.

3. **🤖 Model Training & Cross-Validation**
   - Implemented and trained four models:
     - **Random Forest**: An ensemble of decision trees using majority voting.
     - **Extra Trees**: Similar to Random Forest but with increased randomness in splitting.
     - **SVM (RBF Kernel)**: Utilizes a non-linear RBF kernel to handle complex boundaries.
     - **Linear SVC**: A linear classifier that, in our experiments, took the longest time to train.
   - Performed k-fold cross-validation on the training set to estimate performance and mitigate overfitting.

4. **📊 Model Evaluation**
   - Evaluated each model on the validation set using accuracy, classification reports, and confusion matrices.
   - Found that **Extra Trees** achieved the best overall performance (~97% test accuracy), followed closely by Random Forest.
   - Recorded final test accuracies for all four models for a comprehensive comparison.

5. **🚀 Deployment with Streamlit**
   - Developed a Streamlit app where users can draw a digit directly in the browser.
   - The drawn image is preprocessed (resized to 28×28, normalized) and fed into the trained model.
   - The app displays the predicted digit in real time along with an optional probability distribution.

---

## 📂 Data
- **Source**: [MNIST Dataset](http://yann.lecun.com/exdb/mnist/), loaded via `fetch_openml('mnist_784')`.
- **Format**: Each image is 28×28 pixels, flattened into a 784-dimensional feature vector.
- **Size**: 70,000 images (digits 0–9).

---

## 🤔 Models

### 🌳 Random Forest
- Constructs multiple decision trees on random subsets of data/features.
- Aggregates predictions using majority voting.
- Balances accuracy and speed well, achieving around **97%** accuracy on MNIST in our experiments.

### 🌱 Extra Trees
- Similar to Random Forest but with increased randomness when splitting nodes.
- Demonstrated the best overall performance on the validation set.
- Achieved approximately **97%** accuracy on the MNIST test set.

### 🏆 SVM (RBF Kernel)
- Uses a non-linear RBF kernel to capture complex decision boundaries.
- Achieves high accuracy (around **96–97%**) but requires more computation compared to tree-based methods.

### 📐 Linear SVC
- Typically considered efficient for high-dimensional data.
- In my experiments, however, Linear SVC took the **longest time** to train.
- Its accuracy (~96%) was slightly lower than that of the ensemble methods.

---

## 🎨 Streamlit App
- **Interactive Digit Drawing**: Users can draw a digit on a canvas directly in their browser.
- The drawn image is converted to a 28×28 grayscale image, normalized, and passed to the trained model.
- Real-time predictions are displayed, providing an intuitive demonstration of the model’s performance.

**To run the app:**
```bash
streamlit run app.py
