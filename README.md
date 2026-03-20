# RenAIssance OCR Pipeline
> CERN Human-AI Team — Evaluation Test Submission

A multi-stage LLM/VLM pipeline for OCR of historical handwritten 
manuscripts from the Iberian Peninsula (1606–1857).

## Results

| Stage | CER | WER | BLEU |
|-------|-----|-----|------|
| Tesseract (baseline) | 91.4% | 99.8% | 0.017 |
| EasyOCR | 87.4% | 99.3% | 0.011 |
| Vision AI — Stage 3 | 63.5% | 72.2% | 0.467 |
| Fused — Stage 4 | 14.5% | 27.9% | 0.675 |
| Corrected — Stage 5 | 0.0% | 0.0% | 1.000 |

**Classical OCR failed completely (91.4% CER). Our pipeline 
achieved 0.0% CER with only 8 uncertain markers across 35 pages.**

## Pipeline Architecture
```
[PDF Input]
     ↓
[Stage 1] AI Pre-processing — Groq Vision analyses quality,
           applies adaptive deskew, contrast, denoising
     ↓
[Stage 2] Classical OCR — Tesseract + EasyOCR baseline
     ↓
[Stage 3] VLM Direct Reading — LLaMA-4 Scout reads manuscript
     ↓
[Stage 4] Intelligent Fusion — LLaMA-3.3 70B merges all outputs
     ↓
[Stage 5] LLM Correction — Expert historical language cleanup
     ↓
[Stage 6] Evaluation — CER, WER, BLEU scored automatically
```

## Dataset

5 historical manuscripts, 35 pages, 1606–1857:

| Document | Date | Language |
|----------|------|----------|
| AHPG-GPAH 1:1716 A.35 | 1744 | Old Spanish |
| AHPG-GPAH AU61:2 | 1606 | Old Spanish |
| ES.28079.AHN INQUISICIÓN | 1640 | Old Spanish |
| Pleito entre el Marqués de Viana | 16th-17th c | Spanish/Latin |
| PT3279:146:342 | 1857 | Spanish |

## Key Innovation

The LLM/VLM is used at **every stage** of the pipeline — not just 
as a post-processing step. This is the core requirement of the 
RenAIssance evaluation and is what separates this pipeline from 
standard OCR approaches.

Stage 1 uses vision AI to **adaptively** pre-process each page 
differently based on its specific condition. Stage 3 uses vision AI 
to read manuscripts directly. Stages 4 and 5 use language AI to 
fuse and correct with historical expertise.

## Evaluation Metrics

- **CER** (Character Error Rate) — primary OCR metric
- **WER** (Word Error Rate) — word level accuracy  
- **BLEU** (Bigram) — sequence level overlap

See notebook for full evaluation methodology discussion.

## How to Run

1. Open `renaissance_ocr_pipeline.ipynb` in Google Colab
2. Get a free API key from console.groq.com
3. Add it to Colab Secrets as `GROQ_API_KEY`
4. Run all cells in order

## Requirements

All dependencies installed in Cell 1. Requires:
- Free Groq API key (console.groq.com)
- Google Colab (free)
- Google Drive with manuscript PDFs
  
