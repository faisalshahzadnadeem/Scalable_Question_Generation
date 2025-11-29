# Scalable Question Generation System

A powerful and scalable system for automatically generating multiple-choice questions (MCQs) from PDF and text documents using Google's Gemini AI.

## 📋 Overview

This system processes educational content (lecture transcripts, textbooks, articles) and generates high-quality multiple-choice questions with the following features:

- **Document Processing**: Extracts text from PDF and TXT files
- **Intelligent Chunking**: Splits large documents into manageable sections
- **AI-Powered Generation**: Uses Google Gemini to create contextually relevant questions
- **Quality Control**: Validates questions against source content
- **Difficulty Classification**: Automatically categorizes questions as Easy, Medium, or Hard
- **Export Ready**: Outputs questions in JSON format for easy integration

## 🚀 Features

- **Multi-format Support**: Works with PDF and text files
- **Scalable Architecture**: Processes large documents through intelligent chunking
- **Quality Assurance**: Built-in validation to ensure question relevance
- **Difficulty Assessment**: Classifies questions using Bloom's Taxonomy principles
- **Batch Processing**: Generates multiple questions per document chunk
- **Easy Export**: Download generated questions as JSON files

## 🛠️ Installation & Setup

### Prerequisites
- Python 3.7+
- Google Colab environment (recommended)
- Google Gemini API key

### Installation
```bash
pip install google-generativeai pdfplumber langchain faiss-cpu
```

### Configuration
1. Obtain your Gemini API key from [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Configure the API in the notebook:
```python
import google.generativeai as genai
genai.configure(api_key="YOUR_GEMINI_API_KEY")
```

## 📖 Usage

### Step 1: Upload Document
- Run the document upload cell
- Select your PDF or TXT file
- System automatically extracts and previews content

### Step 2: Text Processing
- Document is split into optimal chunks (2500 characters with 200 overlap)
- Adjust chunk size based on document complexity

### Step 3: Question Generation
- Gemini AI processes each chunk to generate MCQs
- Each question includes:
  - Question text
  - 4 multiple-choice options (A, B, C, D)
  - Correct answer
  - Difficulty level
  - Source preview

### Step 4: Quality Control
- **Validation**: Ensures correct answers are supported by source text
- **Difficulty Classification**: AI-classified as Easy, Medium, or Hard
- **Filtering**: Removes low-quality or unsupported questions

### Step 5: Export Results
- Generated questions saved as `generated_mcqs.json`
- Download directly from Colab environment
- JSON structure compatible with most learning management systems

## 📊 Output Format

```json
[
  {
    "question": "Who is teaching the class today, according to the passage?",
    "choices": [
      "A Professor Nathan",
      "B The keynote speaker", 
      "C Delete Kiloton",
      "D An Associate Professor from another department"
    ],
    "answer": "C",
    "id": "q_1_1",
    "source_preview": "Substituting some shooting frozen RNN...",
    "difficulty": "Easy"
  }
]
```

## ⚙️ Customization

### Adjust Question Quantity
Modify the `num_questions` parameter in the generation function:
```python
generate_mcqs_with_gemini(chunk, num_questions=5)
```

### Modify Chunk Size
Adjust text splitting parameters:
```python
splitter = RecursiveCharacterTextSplitter(
    chunk_size=2500,   # Increase for longer context
    chunk_overlap=200,  # Adjust for context continuity
    length_function=len
)
```

### Quality Thresholds
Customize validation logic in `validate_mcq()` function for stricter/looser quality control.

## 🎯 Use Cases

- **Educational Content Creation**: Generate quiz questions from textbooks
- **Corporate Training**: Create assessment questions from training materials
- **Research**: Automate question generation for studies
- **E-learning Platforms**: Bulk question creation for online courses
- **Test Preparation**: Generate practice questions from study materials

## 📈 Performance

- Processes documents of any size through chunking
- Generates 3-5 high-quality questions per chunk
- Automatic filtering maintains question quality
- Scalable for large document collections

## 🔧 Technical Details

- **AI Model**: Google Gemini 2.5 Flash
- **Text Processing**: LangChain Recursive Text Splitter
- **PDF Extraction**: pdfplumber
- **Output Format**: JSON
- **Quality Metrics**: Source validation, difficulty classification

## ⚠️ Limitations

- Requires Gemini API key with sufficient quota
- Quality depends on source document clarity
- Mathematical/scientific notation may require manual verification
- Complex diagrams or images in PDFs are not processed

## 📄 License

This project is designed for educational and research purposes. Please ensure compliance with Google's Gemini API terms of service and copyright regulations for source documents.

## 🤝 Contributing

Feel free to extend this system with:
- Additional file format support
- Enhanced quality metrics
- Different question types (true/false, fill-in-blank)
- Integration with LMS platforms
- Bulk processing capabilities

---

**Note**: Always verify generated questions for accuracy before using in formal assessments. The system provides a scalable starting point that benefits from human review and refinement.
