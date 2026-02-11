# auditability
Model auditability statement
## Indigenous and Low Resource Language focus
bezoku models are designed for Indigenous and Low-Resource languages. 
They are built from first principles from localized training data that has been annotated using the conllu format.
This approach has low levels of technical debt, is cleaner and avoids inheriting any bias from third-party tools.

## 1. NO PRETRAINED EMBEDDINGS
All word and character embeddings use local orhtographies and are built from scratch from conllu annotated corpus. This ensures:
- Full auditability: unbroken audit trail from corpus annotation to model weights
- No inherited biases from opaque upstream pretraining data (Wikipedia, Common Crawl, etc.)
- Tokenization using UTF-8 local orthographies to avoid any external tooling conflicts

## 2. NO EXTERNAL TOKENIZERS
bezoku does not use BPE, WordPiece, SentencePiece or similar subword tokenizers that:
- Prioritize English with 1-byte representations
- Perpetuate vocabulary biases from English centric multilingual pretraining

## 3. MONOLINGUAL CORPUS PRIORITY
Each language model is trained exclusively on single language conllu corpus, ensuring:
- No cross-lingual transfer from high-resource languages, which may prioritise a different (dominant) orthography
- No multilingual model contamination
- Ensuring Indigenous and Low-Resource languages are prioritized

## 4. LOWER TECHNICAL DEBT
The model architecture has clean, linear data pipelines, especially for syntactic model development, especially excluding:
- External pretrained tooling (embeddings, tokenizers, encoders)
- Third-party preprocessing pipelines with opaque processing

## 5. DEBUGGING CLARITY
Fixes to training data, for example when a new UD treebank is published, offer a clean, repeatable model maintenance process:
- Transparent training data which is open source
- Model weights published
- Avoiding data pipeline issues from third-party pretrained embeddings
