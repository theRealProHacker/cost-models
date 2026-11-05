# cost-models

Model files for COST, published as release assets so they stay out of COST's Git. COST's build downloads them and checks each one against a SHA-256 pinned in its source.

## ocr-v1

The two recognizers of COST's scoresheet reader. Each one reads a single move cell: a 1×32×128 grayscale input, with bright ink on black, scaled to [0, 1]. Each outputs CTC logits over 33 classes.

| File | SHA-256 | What it is |
|---|---|---|
| `ours.onnx` | `dae8479debdf41912bae528a724e1ab6a78d42be1d016cdb53350da6805d22f3` | CRNN, 32 frames |
| `pp_distil.onnx` | `2e8e4fb7472c064583b5a455797cf257b50abbc2c8efdcd31a4ad190253cfd5d` | fine-tuned and distilled from PaddleOCR's PP-OCRv6_tiny_rec (Apache-2.0), 24 frames |

Trained on synthetic cells and on the Handwritten Chess Scoresheet dataset (HCS):
Eicher, Farmer, Li, Majid, "Handwritten Chess Scoresheet Recognition Using a Convolutional BiLSTM Network", CBDAR/ICDAR Workshops 2021;
Majid & Eicher, "Digitization of Handwritten Chess Scoresheets with a BiLSTM Network", J. Imaging 8(2):31, 2022.
