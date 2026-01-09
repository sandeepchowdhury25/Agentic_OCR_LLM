# OCR LLM Agent
Extract text from images using a vision model (Qwen2.5-VL) and a text model (Qwen2.5) orchestrated via LangGraph and LangChain.

## What this does
This project uses:
- `agent/tools.py` with a vision model to read an image and extract raw text.
- `main.py` with a text model to coordinate tool usage and return the final text.

Default models:
- Vision: `qwen2.5vl:7b` (set in `agent/tools.py`)
- Text: `qwen2.5:7b` (set in `main.py`)

You can override them with environment variables:
- `OLLAMA_VISION_MODEL`
- `OLLAMA_TEXT_MODEL`

## Project layout
```
ocr-llm-agent/
  agent/
    tools.py
  images/
    chocolate_cake_recipe.png
  main.py
  requirements.txt
  README.md
```

## Prerequisites
- Python 3.13.5
- Ollama installed and available on your PATH

## Install dependencies
Create and activate a virtual environment, then install `requirements.txt`.

PowerShell:
```powershell
python -m venv test_venv
.\test_venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

## Install and run Ollama models
Start the Ollama server, then pull the required models.

```powershell
ollama serve
```

In a new terminal:
```powershell
ollama pull qwen2.5vl:7b
ollama pull qwen2.5:7b
```

Optional: change models via environment variables:
```powershell
$env:OLLAMA_VISION_MODEL="qwen2.5vl:7b"
$env:OLLAMA_TEXT_MODEL="qwen2.5:7b"
```

## Run the app
```powershell
.\test_venv\Scripts\python main.py
```

The script reads `images/chocolate_cake_recipe.png`, extracts text with the vision model, and prints the final text to the console.

## Save output as Markdown
You can store the extracted text as Markdown by redirecting stdout:
```powershell
.\test_venv\Scripts\python main.py > output.md
```


