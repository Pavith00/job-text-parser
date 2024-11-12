# Job Criteria Information Extraction with spaCy

This project uses spaCy, a powerful natural language processing (NLP) library, to extract essential information from job criteria provided in natural language format. The goal is to automate the extraction of key data points like required skills, qualifications, experience, and more from job descriptions. This makes it easier to match job requirements with candidate profiles for eligibility filtering or recruitment processes.

### Table of Contents

1. [Overview](#overview)
2. [Why spaCy?](#why-spacy)
3. [How spaCy is Used in This Project](#how-spacy-is-used-in-this-project)
4. [Code Explanation](#code-explanation)
5. [Installation](#installation)
6. [Usage](#usage)

---

### Overview

In job descriptions, qualifications, required skills, experience, and other criteria are often mentioned in unstructured text. This project builds a model using **spaCy** to extract important data points from this text and turn it into a structured format. By doing so, this system enables better analysis and matching of candidates to job criteria.

The primary use case for this project is automating the extraction of key information from job descriptions, making it easier to analyze and match applicants' qualifications against specific job requirements.

---

### Why spaCy?

**spaCy** is a leading open-source library for natural language processing (NLP). It's fast, efficient, and easy to use for text analysis tasks, making it a perfect choice for extracting structured data from unstructured text like job descriptions.

**Why spaCy?**
- **Pre-trained models**: spaCy provides pre-trained models for various languages, making it easy to apply NLP techniques like part-of-speech tagging, named entity recognition (NER), and dependency parsing.
- **Entity Recognition**: spaCy excels at **named entity recognition (NER)**, which allows the model to identify key pieces of information such as dates, qualifications, skills, and experience mentioned in the job descriptions.
- **Customizable**: It allows easy customization and extension to fine-tune models for specific tasks (like extracting specific job-related criteria).
- **Efficient Processing**: spaCy is optimized for speed and large-scale text processing, making it ideal for real-world applications like job description extraction.

---

### How spaCy is Used in This Project

In this project, spaCy is primarily used for **named entity recognition (NER)** to identify key pieces of information from job descriptions. For instance, the model is trained to identify and extract entities such as:
- **Qualifications**: e.g., "Bachelor's degree in Computer Science"
- **Experience**: e.g., "5 years of experience"
- **Skills**: e.g., "proficiency in Python"
- **Age criteria**: e.g., "must be between 25 and 40 years old"

### Key Steps in Using spaCy:

1. **Loading Pre-trained Models**: We load spaCy's pre-trained language models to process and analyze job criteria text.
2. **Text Processing**: The input job description text is passed through spaCy's NLP pipeline, which applies tokenization, part-of-speech tagging, and dependency parsing.
3. **Named Entity Recognition (NER)**: spaCy's NER is used to detect and classify entities such as dates, skills, qualifications, and experience from the text.
4. **Custom Rules**: You can extend the default entity recognition by adding custom rules tailored to specific job descriptions or criteria (e.g., extracting skill sets or required qualifications).
5. **Output Structured Data**: The extracted entities are then formatted into structured data, which can be used for filtering or analyzing candidates based on job requirements.

---

