# AL Resume Scanner

## Overview
This project is a ** AI Resume Scanner** that uses Natural Language Processing (NLP) techniques to analyze resumes, recommend relevant skills, and suggest courses based on the candidate’s skills. It is built with Python and deployed as a web application using Streamlit. The app allows users to upload their resumes, and based on the content, it processes and outputs useful insights like predicted job fields, recommended skills, and course suggestions.

## Features
- **Resume Upload**: Upload a resume in PDF or text format.
- **Skills Extraction**: Extracts skills from the resume using NLP techniques.
- **Job Field Prediction**: Predicts potential job fields based on extracted skills.
- **Skill Recommendations**: Suggests additional skills for improving the resume.
- **Course Recommendations**: Suggests online courses or certifications based on the skills.

## Tech Stack
- **Streamlit**: For deploying the web application.
- **Python**: Main language used for processing.
- **spaCy / NLTK**: Libraries for Natural Language Processing.
- **Pandas**: For data manipulation and extraction.
- **Plotly**: For visualizations like pie charts.
- **SQLite/MySQL**: For database to store user data (optional).
- **Random**: For randomizing course suggestions.

## Installation

To run this project locally, follow the steps below:

### Step 1: Clone the repository

```bash
git clone https://github.com/yourusername/resume-scanner.git
cd resume-scanner
```

### Step 2: Set up a virtual environment

```bash
python -m venv venv
source venv/bin/activate   # On Windows use `venv\Scripts\activate`
```

### Step 3: Install the required dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Install other required packages for NLP

Make sure to install the `spaCy` language models or any other required dependencies if not already included:

```bash
python -m spacy download en_core_web_sm
```

### Step 5: Run the application

```bash
streamlit run app.py
```

This will start the Streamlit app locally and open it in your browser.

## File Structure

```
├── app.py                # Main file that runs the Streamlit application
├── course.py             # Handles course recommendations logic
├── nlp_processing.py     # Contains NLP methods like skill extraction
├── requirements.txt      # Python package dependencies
├── database/             # Contains the SQLite/MySQL database files
├── assets/               # Contains static assets (icons, logos, etc.)
├── README.md             # Project documentation
└── data/                 # Store any sample data, resumes, etc.
```

## NLP Process

### 1. **Text Preprocessing**
   - The resume text is extracted using **PyPDF2** or any other text extraction method.
   - Text is cleaned by removing unnecessary characters and stop words.
   
### 2. **Skill Extraction**
   - I use **spaCy** to tokenize the text and identify relevant entities that match the list of skills (Data Science, Web Development, etc.).
   - I have pre-defined keyword lists for different fields like `data science`, `web development`, `android development`, etc., and match the extracted skills with these lists.

### 3. **Job Field Prediction**
   - Based on the extracted skills, the system predicts the most relevant job field (Data Science, Web Development, etc.) by matching skills with field-specific keywords.

### 4. **Recommendation System**
   - **Skills Recommendation**: I recommend additional skills that would enhance the candidate’s profile based on the skills extracted from the resume.
   - **Course Recommendation**: Based on the skills extracted, I suggest courses from predefined lists. The recommendations are shown dynamically using the `st.slider` widget.

## Deployment on Streamlit

Streamlit provides an easy and efficient way to deploy Python applications. Here’s a quick rundown of how I deployed the project:

1. **Streamlit Widgets**: The app is built using **Streamlit** and employs interactive widgets like text inputs, sliders, and buttons to allow the user to upload resumes, view results, and get recommendations.
2. **Data Display**: For displaying results like skills, job fields, and course recommendations, **Pandas** is used to manage the data, and **Plotly** is used for generating pie charts.
3. **User Authentication**: I use simple logic to authenticate users for admin access to view user data.
4. **Visualization**: The app shows visual feedback on skill recommendations, predicted job fields, and user data through interactive graphs.

### Streamlit Configuration

- The `streamlit run app.py` command starts the application and automatically opens the app in the browser.
- The app is designed to work on both **light** and **dark modes**, and some basic styling is applied through **custom CSS** to enhance the user interface.

### Base64 Library Overview

The **`base64`** library in Python is used to encode and decode binary data into a text representation, commonly known as Base64 encoding. This encoding method is widely used to handle data in systems that need to store or transfer binary data, such as images, audio files, or file uploads in text-based formats like JSON or HTML. The **`base64`** module allows you to easily convert binary data into a readable and transferable format, ensuring safe and efficient transmission across systems that might not support raw binary formats.

### Key Features:
- **Base64 Encoding**: Converts binary data (e.g., images, files) into a safe, readable ASCII string format.
- **Base64 Decoding**: Converts the encoded Base64 string back to its original binary data.
- **Secure Data Transmission**: Ensures that binary data can be safely transmitted in text-based protocols (e.g., email, JSON).
- **Simple API**: Provides functions like `base64.b64encode()` and `base64.b64decode()` for easy encoding and decoding.

## Future Enhancements
- **Improved Skill Extraction**: Enhance the NLP process to identify even more skills and improve accuracy.
- **Multi-language Support**: Extend the app to support resumes in different languages.
- **Resume Scoring**: Add an automated resume scoring feature based on keyword matching and field-specific criteria.
- **User Authentication**: Implement a more advanced user authentication system using OAuth or similar.
- **Cloud Deployment**: Deploy the app on cloud platforms like **Heroku**, **AWS**, or **Azure** for production use.
