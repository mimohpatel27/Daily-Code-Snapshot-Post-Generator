# Daily-Code-Snapshot-Post-Generator
The agent takes a screenshot of your code, extracts the code automatically, understands what the code does, and generates a clean, structured #300DaysOfCode daily update post.


# Daily Code Snapshot → Post Generator Agent

**Automatically convert a screenshot of your code into a ready-to-post `#300DaysOfCode` update.**

---

## Table of Contents
- [Problem](#problem)  
- [Why Agents?](#why-agents)  
- [Solution Overview](#solution-overview)  
- [Architecture](#architecture)  
- [Demo](#demo)  
- [Usage](#usage)  
  - [Quick Colab run (recommended)](#quick-colab-run-recommended)  
  - [Local setup (Linux / macOS)](#local-setup-linux--macos)  
- [Files in this repo](#files-in-this-repo)  
- [Expected Output Example](#expected-output-example)  
- [Troubleshooting & Tips](#troubleshooting--tips)  
- [Future Work](#future-work)  
- [Contributing](#contributing)  
- [License](#license)

---

## Problem
Creating daily `#300DaysOfCode` posts is repetitive and takes time. Developers must:
- extract code (often from screenshots),
- summarize what the code does,
- write a concise explanation of the approach,
- add a useful tip and hashtags.

This overhead breaks consistency and reduces the habit-forming value of daily posting.

---

## Why Agents?
A single script cannot reliably handle the perception + reasoning chain needed here. The workflow requires:
1. vision (OCR on screenshots),  
2. code understanding (language detection, algorithm extraction),  
3. natural-language generation (concise human-like posts),  
4. output formatting per platform.

An AI agent (OCR + LLM) can chain these steps, adapt to noisy inputs, and produce consistent high-quality posts at scale.

---

## Solution Overview
**Daily Code Snapshot → Post Generator Agent** accepts a screenshot, preprocesses it, extracts code via OCR, cleans and detects the language, sends the cleaned code to a generative model (Gemini), and returns a structured social-post containing:
- Hook  
- Summary  
- Approach explanation  
- Tip / insight  
- Hashtags

This pipeline is implemented as a Colab notebook (fast demo) and as standalone Python modules (for local use).

---

## Architecture

<img width="342" height="637" alt="Ai Agent flow chart  drawio" src="https://github.com/user-attachments/assets/333e3e4e-74b4-4530-94d1-b4da3aa374d7" />


**Components**
- Upload Module — file input (Colab `files.upload()` or local file path)  
- Preprocessing — grayscale, resize, denoise, adaptive thresholding (OpenCV)  
- OCR — Pytesseract  
- Cleaner — regex rules to extract code-like lines and rebuild indentation  
- Detector — Pygments-based language identification  
- Generator — Gemini (google-genai) with structured prompt (JSON output expected)  
- Exporter — writes a `.txt` file and prints the post for copy-paste

> Add a visual diagram file at `assets/architecture.png` (recommended). A placeholder `assets/demo.gif` can demonstrate the notebook flow.

---

## Demo

**What you will see:**
1. Upload screenshot (button appears in Colab).  
2. Notebook shows OCR raw text and cleaned code.  
3. Model output printed as JSON-like block.  
4. Final stylized post shown and saved as `post_YYYYMMDD_HHMMSS.txt`.

**Placeholders in repo**  
- `/assets/sample_screenshot.png` — example screenshot used in demos  
- `/assets/sample_output.txt` — sample final post  
- `/assets/demo.gif` — short demo GIF (upload manually)

---

## Usage

### Quick Colab run (recommended)
1. Open Colab and create a new notebook or use the provided `notebook.ipynb`.  
2. Run these cells in order:

```python
# Cell 1 - Install dependencies
!pip install google-genai pytesseract opencv-python-headless pillow numpy pygments

# Cell 2 - Install tesseract binary (Colab)
!apt-get update -qq
!apt-get install -y -qq tesseract-ocr libtesseract-dev

# cell 3- Set your Gemini API key (replace with your key):
!import os
!os.environ["GEMINI_API_KEY"] = "YOUR_GEMINI_API_KEY"

#cell 4 - Run the notebook cells (imports, upload, preprocess, OCR, generate).

Upload via the visible button (Colab files.upload()).

The notebook will output the post and create a downloadable .txt file.

!git clone https://github.com/YOUR_USER/daily-code-snapshot-agent.git
!cd daily-code-snapshot-agent
!python3 -m venv venv
!source venv/bin/activate
!pip install -r requirements.txt
!google-genai
!pytesseract
!opencv-python-headless
!pillow
!pygments
!numpy
!sudo apt-get update
!sudo apt-get install tesseract-ocr
!brew install tesseract
!export GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
!python run_agent.py --image assets/sample_screenshot.png --tone Casual --platform LinkedIn




🔥 Day 308 of #300DaysOfCode — Reinforced DP fundamentals!

Summary:
I solved the "largest square of 1s in a binary matrix" using dynamic programming. The core idea is to build a DP table and compute each cell's value based on its top/left/top-left neighbors.

Approach:
- Bottom-up DP table
- Cell value = min(top, left, top-left) + 1 if cell==1
- Track max as you iterate (O(m*n) time)

Hashtags:
#300DaysOfCode #Java #DynamicProgramming #CodingJourney
