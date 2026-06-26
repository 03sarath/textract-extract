# AWS Textract — Document Text Extraction Demo

Simple, UI-free document text extraction for GenAI/RAG ingestion. Upload a document → get clean text back. (RAG itself is **not** built here — this is the extraction step only.)

## Files
| File | What it is |
|---|---|
| `textract_extract.ipynb` | The demo notebook. Sync `DetectDocumentText`, no S3 needed. Upload widget + path option. Azure & GCP reference examples are in markdown cells at the bottom. |
| `requirements.txt` | Python dependencies. |

## Run it
```bash
pip install -r requirements.txt
jupyter notebook textract_extract.ipynb
```
Then run the cells top to bottom: upload a `PNG/JPEG/TIFF/single-page PDF`, and the text prints out (and saves to `<name>_extracted.txt`).

## Prerequisites
- AWS CLI already authenticated (you confirmed this). The notebook uses your default credential chain — verify with `aws sts get-caller-identity`.
- IAM permission: `textract:DetectDocumentText` (and `textract:AnalyzeDocument` for the optional forms cell).
- Region defaults to `us-east-1` — change `AWS_REGION` in the config cell if needed.

## Scope
- **Sync only:** 1 page / 10 MB max. Multi-page PDFs need the async S3-based API — noted at the bottom of the notebook, deliberately left out to keep this simple.
