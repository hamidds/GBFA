# Farsi Gender Bias Evaluation Datasets

This repository contains the Farsi-translated datasets used in the paper "Measuring Gender Bias in Language Models in Farsi" by Saffari et al., accepted at the GebNLP workshop for ACL 2025. These datasets represent the first comprehensive evaluation framework for detecting gender bias in Farsi language models across three distinct tasks.

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

```bibtex

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

## 🤝 Contributing

We welcome contributions to improve and extend these datasets:
- Additional validation by native speakers
- Cultural adaptation of evaluation frameworks
- Extension to non-binary gender categories
- Manual translation improvements

## 📞 Contact

- **Hamidreza Saffari**: hamidreza.saffari@mail.polimi.it
- **Mohammadamin Shafiei**: m.shafieiapoorvari@studenti.unimi.it  
- **Donya Rooein**: donya.rooein@unibocconi.it
- **Debora Nozza**: debora.nozza@unibocconi.it

## 🏛️ Affiliations

- Politecnico di Milano
- University of Milan  
- Bocconi University

## 📄 License

[Add appropriate license information]

## 🙏 Acknowledgments

This research is supported by:
- European Research Council (ERC) under Horizon 2020 (grant agreement No. 101116095, PERSONAE)
- ERC under Horizon 2020 (grant agreement No. 949944, INTEGRATOR)
- MilaNLP group and BIDSA at Bocconi University

---

**Note**: This work represents an important step toward more inclusive bias research in underrepresented languages. We encourage responsible use of these datasets and welcome collaboration to further advance fairness in NLP for diverse linguistic communities. 
