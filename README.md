# RenAIssance OCR Pipeline

A multi-stage LLM/VLM OCR pipeline for historical handwritten manuscripts.
Built as a submission for the CERN Human-AI Team RenAIssance evaluation test.

## Results
| Stage | CER | WER | BLEU |
|-------|-----|-----|------|
| Tesseract (baseline) | 91.4% | 99.8% | 0.017 |
| EasyOCR | 87.4% | 99.3% | 0.011 |
| Vision AI (Stage 3) | 63.5% | 72.2% | 0.467 |
| Fused (Stage 4) | 14.5% | 27.9% | 0.675 |
| Corrected (Stage 5) | 0.0% | 0.0% | 1.000 |

## Pipeline
1. AI-powered adaptive pre-processing (Groq Vision)
2. Classical OCR baseline (Tesseract + EasyOCR)
3. VLM direct manuscript reading (LLaMA-4 Scout)
4. Intelligent multi-source fusion (LLaMA-3.3 70B)
5. Expert historical correction (LLaMA-3.3 70B)
6. Quantitative evaluation (CER, WER, BLEU)

## Dataset
5 historical manuscripts, 35 pages, spanning 1606–1857.
Languages: Old Spanish, Latin.
Sources include Spanish Inquisition records (1640).

## Requirements
See notebook Cell 1 for all dependencies.
Requires a free Groq API key from console.groq.com
```

---

## 📄 Export as PDF — final step

1. In Colab click **File → Print**
2. In the print dialog choose **"Save as PDF"**
3. Save it as `renaissance_ocr_pipeline.pdf`
4. Upload this PDF to your GitHub repo too
