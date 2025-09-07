---
title: "AI-Powered Phishing Email Detector"
excerpt: "An in-progress project building a command-line tool in Python that uses NLP and machine learning to classify emails as phishing or legitimate."
collection: portfolio
---

To merge my skills in software development with my passion for cybersecurity, I am developing a machine learning application to automatically detect phishing attempts based on email content. The goal is an interactive command-line tool that can analyze pasted text and return a real-time prediction, showcasing a practical application of AI in defensive security.

### Project Status: In Development

This project is a work-in-progress. The core architecture and machine learning pipeline—from data preprocessing to model prediction—are functionally complete. The primary task remaining is to source and integrate a large, high-quality dataset of phishing and legitimate emails to properly train and validate the model's performance.

The main objectives of this project are to:
1.  Build an end-to-end text classification pipeline using Python.
2.  Gain hands-on experience with key NLP libraries (`NLTK`) and machine learning frameworks (`Scikit-learn`).
3.  Create a modular, reusable code structure for a machine learning application.

---

### The Implemented Machine Learning Pipeline

The application follows a standard pipeline to transform raw text into an actionable prediction.

#### 1. Data Preprocessing
To prepare unstructured email text for analysis, I built a preprocessing function using **NLTK** that:
*   Removes all punctuation and non-alphabetic characters.
*   Converts all text to lowercase for consistency.
*   Filters out common English "stop words" (e.g., 'the', 'a', 'is').
*   Applies **stemming** to reduce words to their root form (e.g., "congratulations" becomes "congratul").

This cleaning step is crucial for helping the model focus on the words that are most indicative of malicious intent.

#### 2. Feature Extraction with TF-IDF
A machine learning model cannot understand words directly. I used the **TF-IDF (Term Frequency-Inverse Document Frequency)** technique from **Scikit-learn** to convert the cleaned text into numerical vectors. TF-IDF is effective because it gives higher weight to words that are frequent in a specific email but rare across all other emails, helping to identify unique and potentially suspicious keywords.

#### 3. Model Training and Prediction
I chose a **Logistic Regression** model for its efficiency and interpretability. The `train.py` script orchestrates the entire process: loading data, running preprocessing and vectorization, and training the model. The trained model and vectorizer are then saved as `.pkl` files.

The `main.py` script provides an interactive command-line interface that loads these saved files to make instant predictions on new, unseen email text, complete with a confidence score.

---

### Key Skills Practiced & Demonstrated
*   **Machine Learning:** End-to-end implementation of a text classification pipeline.
*   **Natural Language Processing (NLP):** Text cleaning, stop word removal, stemming, and TF-IDF vectorization.
*   **Python Programming:** Modular and clean code structure with separate components for data processing, modeling, and prediction.
*   **Core Libraries:** Proficient use of **Scikit-learn**, **NLTK**, and **Pandas**.
*   **Software Design:** Creation of a reusable and extensible machine learning application.

### Future Roadmap
With the foundation in place, my next steps are to:
*   **Source and Integrate a Dataset** to train and validate the model.
*   Experiment with other models like Naive Bayes or Support Vector Machines (SVMs).
*   Perform hyperparameter tuning to optimize model performance.
*   Develop a simple web interface using Flask or Streamlit for a more user-friendly experience.

The complete source code, including the modular pipeline structure, is available on my GitHub.

[**View the Project on GitHub**](https://github.com/busch-l/AI-Phishing-Detector)