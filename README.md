# Farsi Gender Bias Evaluation Datasets

This repository contains the Farsi-translated datasets used in the paper *"Measuring Gender Bias in Language Models in Farsi"* ([paper link](https://aclanthology.org/2025.gebnlp-1.21/)). These datasets represent the first comprehensive evaluation framework for detecting gender bias in Farsi language models across three distinct tasks.

The paper was published in the *Proceedings of the 6th Workshop on Gender Bias in Natural Language Processing (GeBNLP)* at ACL 2025.

## 📋 Overview

This work introduces adapted versions of three established English bias evaluation frameworks for Farsi:
- **Emotion Analysis**: Based on the [ISEAR dataset](https://www.unige.ch/cisa/research/materials-and-online-research/research-material/) for gendered emotion attribution
- **Question Answering**: Adapted from [BBQ (Bias Benchmark for QA)](https://github.com/nyu-mll/BBQ) 
- **Hurtful Completions**: Translation of the [HONEST framework](https://github.com/MilaNLProc/honest)

## 📊 Datasets

### 1. Farsi ISEAR - Emotion Analysis
- **File**: `ISEAR-Fa.csv`
- **Source**: [International Survey On Emotion Antecedents And Reactions (ISEAR)](https://www.unige.ch/cisa/research/materials-and-online-research/research-material/)
- **Size**: 3,552 samples (500 per emotion × 7 emotions)
- **Columns**: 
  - `SEX`: Gender code (1=male, 2=female)
  - `SEX_MAP`: Gender label (male/female)
  - `EMOT`: Emotion code (1-7)
  - `id`: Sample identifier
  - `SIT`: Original English event description
  - `SIT_Persian`: Farsi translated event description
- **Emotions**: joy, fear, anger, sadness, disgust, shame, guilt
- **Purpose**: Evaluate gendered emotion attribution in language models

### 2. Farsi BBQ - Question Answering
- **File**: `BBQ-Fa.csv`
- **Source**: [Bias Benchmark for QA (BBQ)](https://github.com/nyu-mll/BBQ) - Gender identity category
- **Size**: 208 samples (binary gender only)
- **Structure**: 
  - Ambiguous contexts (insufficient information)
  - Disambiguated contexts (clear distinguishing details)
  - Negative and non-negative questions
- **Purpose**: Assess gender bias in QA through stereotype-based reasoning

### 3. Farsi HONEST - Hurtful Completions
- **File**: `HONEST-Fa.csv`
- **Source**: [HONEST evaluation framework](https://github.com/MilaNLProc/honest)
- **Size**: 960 templates
- **Columns**:
  - `template_masked`: Farsi template with [M] placeholder
  - `raw`: Template format with {} placeholder
  - `identity`: Farsi gender identity term
  - `number`: Singular/plural
  - `category`: Gender category (male/female)
  - `type`: Template type (occupation)
- **Components**: 
  - 14 male and 14 female identity terms
  - 15 different predicates
  - Cloze sentence templates
- **Purpose**: Measure hurtful stereotype generation in language models

## 🔬 Translation & Validation

### Translation Process
- **Method**: Automatic translation using Claude (claude-3-5-haiku-20241022)
- **Approach**: Direct translation maintaining semantic accuracy
- **Quality Control**: Professional translation prompt ensuring natural Farsi

### Validation
- **Validators**: Three native Farsi speakers from Iran
- **Coverage**: 
  - 100 random samples from ISEAR dataset
  - 100 random samples from BBQ dataset  
  - All templates from HONEST dataset (given smaller size)
- **Results**: All translations deemed semantically accurate despite minor grammatical variations

## 📁 Repository Structure

```
├── ISEAR-Fa.csv          # Emotion analysis dataset
├── BBQ-Fa.csv            # Question answering bias dataset
├── HONEST-Fa.csv         # Hurtful completion templates
└── README.md             # This file
```

## 📋 Experimental Details

### Models Evaluated
- **Generative Models**: Llama-2-7b, Meta-Llama-3-8B, Mistral-7B-Instruct-v0.3
- **Encoder Models**: ParsBERT, FaBERT, AriaBERT
- **Settings**: Zero-shot evaluation, temperature=0

### Tasks
1. **Emotion Attribution**: Gendered persona adoption for emotion prediction
2. **Stereotype Assessment**: Bias measurement in ambiguous vs. disambiguated contexts  
3. **Toxicity Analysis**: Hurtful completion generation across gender templates

## 🎯 Key Findings

- Gender bias patterns in Farsi differ from English, highlighting language-specific cultural factors
- Stereotypical positive emotions more often attributed to women
- Negative/internalized emotions more frequently linked to men
- Higher toxicity rates observed in Farsi models compared to other languages
- Significant gender disparities in hurtful completion generation

## 📝 Citation

If you use these datasets in your research, please cite:

```
@inproceedings{saffari-etal-2025-measuring,
    title = "Measuring Gender Bias in Language Models in {F}arsi",
    author = "Saffari, Hamidreza  and
      Shafiei, Mohammadamin  and
      Rooein, Donya  and
      Nozza, Debora",
    editor = "Fale{\'n}ska, Agnieszka  and
      Basta, Christine  and
      Costa-juss{\`a}, Marta  and
      Sta{\'n}czak, Karolina  and
      Nozza, Debora",
    booktitle = "Proceedings of the 6th Workshop on Gender Bias in Natural Language Processing (GeBNLP)",
    month = aug,
    year = "2025",
    address = "Vienna, Austria",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2025.gebnlp-1.21/",
    pages = "228--241",
    ISBN = "979-8-89176-277-0"
}
```

## ⚖️ Ethics & Limitations

### Acknowledged Limitations
- **Binary Gender Focus**: This study is limited to binary gender representation due to resource constraints
- **Translation Bias**: Automatic translation may introduce additional biases
- **Cultural Framework**: English-centric evaluation frameworks may miss Iranian/Islamic cultural contexts
- **Western Bias**: Some concepts (e.g., "seven deadly sins") reflect Western rather than Iranian cultural frameworks

### Ethical Considerations
- Focus on representational harms and stereotype perpetuation
- Systematic investigation of gender bias across multiple tasks
- Transparent reporting of limitations and potential biases
- Contribution to more inclusive NLP research for underrepresented languages


---
If you have any questions, do not hesitate to contact hamidreza.saffari@mail.polimi.it
