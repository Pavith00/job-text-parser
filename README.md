# **SpaCy NER for CV Criteria Extraction**

## **Project Overview**

This project uses the **spaCy** library, a powerful and efficient tool for Natural Language Processing (NLP), to extract structured information from unstructured text in CVs or other documents. Specifically, we are training a Named Entity Recognition (NER) model to identify key criteria (like age, O/L qualifications, and A/L qualifications) from a given text. This structured data is then used to filter and evaluate applicants based on pre-defined job criteria.

---

## **What is spaCy?**

[spaCy](https://spacy.io/) is an open-source library for advanced NLP in Python. It is designed specifically for production use, with an emphasis on speed, efficiency, and ease of use. spaCy provides robust models for various NLP tasks, including tokenization, part-of-speech tagging, dependency parsing, and named entity recognition (NER).

### **Key Features:**
- **Fast and Efficient**: Built for performance, spaCy can process large text datasets quickly.
- **Pre-trained Models**: spaCy provides pre-trained models for various languages that can be fine-tuned for specific tasks.
- **Customizable Pipelines**: You can create custom NLP pipelines for specific use cases, such as NER, text classification, and more.
- **Entity Recognition**: spaCy excels in extracting entities (e.g., dates, names, locations) from text, which is central to this project.

---

## **Why Use spaCy in This Project?**

We are using spaCy to extract specific information (such as age, O/L sitting results, A/L qualifications, etc.) from text-based job criteria. These entities will be used to filter applicants based on their qualifications and eligibility.

In particular, **Named Entity Recognition (NER)** is essential in this project, as we need to identify and categorize certain entities in the CVs, such as:
- Age
- O/L Sitting Results
- A/L Qualifications
- London O/L and A/L qualifications

spaCy's NER pipeline will be trained on labeled data from our CSV file, enabling it to accurately extract these entities from complex job criteria text.

---

## **How spaCy is Used Here**

### **1. Data Preparation**
We first load a CSV dataset containing job criteria with fields such as:
- Age criteria
- O/L sitting results
- A/L qualifications

The data is then processed to create training examples in a format that spaCy can understand, where each piece of information in the text (like "aged 30 or 35" or "6 passes in 1 sitting") is labeled with a specific category.

### **2. Training the NER Model**
- We initialize a blank spaCy model with the English language (`spacy.blank("en")`).
- The **NER pipeline** is added to the model, and labels for the entities we wish to extract (such as `"AGE_CRITERIA"`, `"OL_SITTING"`, etc.) are defined.
- Training data is created by matching the job criteria values in the text to these predefined labels.
- We train the model using the **minibatch** function, which processes the training data in small batches to improve efficiency.
- The model is updated with each batch of training data, and losses are monitored to ensure the model improves over time.

### **3. Evaluation and Inference**
Once the model is trained, we test it by passing in example text (e.g., job requirements like "Applicants must be aged 30 or 35..."). The model then extracts the entities, and the extracted entities are printed with their corresponding labels.

### **4. Saving and Loading the Model**
After training, the model is saved to Google Drive for later use. We can load this saved model whenever we need to process new text and extract relevant entities.

---

## **Project Structure**

```
CV_Project/
│
├── criteria.csv             # The CSV file containing job criteria and applicants' qualifications
├── criteria_ner_model/      # Folder to store the trained NER model
│   └── <model files>        # Files for the trained spaCy model
├── train_spacy_model.py     # Script to train the spaCy NER model
└── README.md                # This README file
```

---

## **Installation and Setup**

1. **Install spaCy**:
   To use this project, first install the spaCy library:
   ```bash
   pip install spacy
   ```

2. **Download Language Model**:
   spaCy uses pre-trained models for processing text. For this project, we use the blank English model (`en_core_web_sm`).
   ```bash
   python -m spacy download en_core_web_sm
   ```

3. **Mount Google Drive**:
   To access the dataset and save the trained model, mount your Google Drive in your environment:
   ```python
   from google.colab import drive
   drive.mount('/content/drive', force_remount=True)
   ```

4. **Run the Training Script**:
   To train the model, run the `train_spacy_model.py` script:
   ```bash
   python train_spacy_model.py
   ```

5. **Test the Model**:
   After training, you can test the model by loading it and running a sample input:
   ```python
   nlp = spacy.load("/path/to/criteria_ner_model")
   test_text = "Applicants must be aged 30 or 35 as of the application closing date..."
   doc = nlp(test_text)
   for ent in doc.ents:
       print(ent.text, ent.label_)
   ```

---

## **Conclusion**

This project demonstrates how spaCy can be applied to extract key criteria from job requirement text. By training a custom NER model, we can automate the process of identifying and categorizing relevant information in CVs, making it easier to filter applicants based on their qualifications and job criteria.

---

