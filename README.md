# CV Parser & Scorer

A Python-based CV/Resume parsing system that extracts information from PDF resumes and scores candidates based on AI/ML expertise and technical skills.

## Features

- **PDF Text Extraction**: Handles both text-based and scanned PDFs (with OCR support)
- **Information Extraction**: Automatically extracts contact details, work experience, education, and skills
- **AI/ML-Focused Scoring**: Specialized scoring algorithm for AI and machine learning roles
- **Batch Processing**: Process multiple CVs in one go
- **Multiple Export Formats**: Export results to Excel or JSON
- **Ranking System**: Automatically ranks candidates and assigns tiers

## Installation

```bash
pip install pdfplumber pandas openpyxl

# Optional: For OCR support
pip install pytesseract pdf2image
python -m spacy download en_core_web_sm
```

## Usage

### Command Line

```bash
# Process a single CV
python cv_parser.py resume.pdf

# Process a folder
python cv_parser.py resumes_folder/

# Export to JSON
python cv_parser.py resumes_folder/ --json
```

### As a Library

```python
from cv_parser import CVParser

parser = CVParser(output_dir="results")
parser.process_folder("resumes/")
parser.export_excel()

# Get top candidates
top_10 = parser.get_top(10)
```

## Scoring System

| Category | Weight | Examples |
|----------|--------|----------|
| AI/ML Core | 10 | machine learning, deep learning, NLP |
| AI Frameworks | 8 | TensorFlow, PyTorch, Keras |
| Cloud ML | 7 | AWS SageMaker, Azure ML, GCP |
| Data Science | 6 | pandas, numpy, MLOps |
| Programming | 5 | Python, R, C++, Java |
| General Dev | 3 | Git, CI/CD, REST API |

**Experience Multipliers:** 0-2 years (1.0x) | 2-5 years (1.3x) | 5-10 years (1.6x) | 10+ years (2.0x)

**Bonus Points:** GitHub (+20) | LinkedIn (+10) | Portfolio (+5 each)

## Output

- Excel/JSON exports with rankings and scores
- Extracted: contact info, skills, experience, education
- Automated tier assignment (Top 10%, 25%, 50%)

## Customization

Edit `SCORING_CONFIG` and `EXPERIENCE_MULTIPLIERS` in `cv_parser.py` to adjust weights and keywords.
