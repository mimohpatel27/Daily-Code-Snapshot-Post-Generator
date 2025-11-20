# Daily Code Snapshot → Post Generator Agent

Automatically convert a screenshot of your code into a polished, ready-to-post **#300DaysOfCode** update using OCR + Gemini + intelligent content generation.

---

## 📚 Table of Contents
- [Problem](#-problem)
- [Why Agents?](#-why-agents)
- [What I Created — Overall Architecture](#-what-i-created--overall-architecture)
- [Demo — How It Works](#-demo--how-it-works)
- [The Build — Tools & Technologies](#-the-build--tools--technologies)
- [Usage](#-usage)
  - [Google Colab (Recommended)](#google-colab-recommended)
  - [Local Setup](#local-setup)
- [Files in This Repository](#-files-in-this-repository)
- [Troubleshooting](#-troubleshooting)
- [If I Had More Time](#-if-i-had-more-time)
- [License](#-license)

---

## 🚩 Problem
Writing daily **#300DaysOfCode** posts is repetitive and time-consuming. Summarizing code, explaining the logic, generating captions, adding insights, and formatting hashtags every day becomes overwhelming. This friction leads to inconsistency—even when coding work is actually done.

---

## 🤖 Why Agents?
This workflow demands **perception + reasoning + structured generation**:

- Reading screenshots (vision)
- Extracting text via OCR
- Cleaning noisy code output
- Detecting programming language
- Understanding logic behind the code
- Summarizing the solution
- Formatting a social-ready daily post

Traditional scripts cannot handle this complexity.  
A **reasoning agent** can chain multiple tasks, adapt to different screenshot styles, and produce consistent high-quality output—reducing friction while maintaining daily posting discipline.

---

## 🏗️ What I Created — Overall Architecture

<img width="342" height="637" alt="Ai Agent flow chart  drawio" src="https://github.com/user-attachments/assets/6bdf01af-2af1-4e08-b517-08fef2df48ba" />


### Core Components:
- Screenshot upload module (Colab button)
- Image preprocessing (grayscale, thresholding, denoising)
- OCR via Tesseract
- Intelligent code-cleaning engine
- Programming language detection
- Post generation via Gemini (hook → summary → approach → tip → hashtags)
- Export to `.txt` for LinkedIn/Twitter/Instagram sharing

---

## 🎬 Demo — How It Works

1. **Upload** a screenshot of your code.
2. The agent runs preprocessing → OCR → code cleaning.
3. Code language is auto-detected.
4. Clean code is sent to **Gemini 2.5 Flash**, which generates:
   - A catchy hook  
   - Clear summary  
   - Approach explanation  
   - One useful coding tip  
   - Optimized hashtags  
5. Final output appears on screen and is saved as a `.txt` file.

### Example Output:

Day 308 of #300DaysOfCode — Strengthening my DP fundamentals!

Summary:
Solved the Largest Square of 1s problem using dynamic programming.

Approach:

Bottom-up DP table

Cell = min(top, left, top-left) + 1

O(m*n) time complexity

Tip:
Add boundary padding to simplify index checks.

Hashtags:
#300DaysOfCode #Java #DynamicProgramming #CodingJourney #DSA


---

## 💻 The Build — Tools & Technologies

- **Python 3**
- **Google Colab** (easy interface + upload)
- **google-genai (Gemini 2.5 Flash)**
- **OpenCV** (image preprocessing)
- **Pytesseract** (OCR extraction)
- **PIL/Pillow** (image handling)
- **Pygments** (language detection)
- **Regex** (noise removal & code fixing)
- **JSON Processing** (clean structured output)

Everything is modular, with each step testable independently.

---

## 🚀 Usage

### Google Colab (Recommended)

1. Open `notebook.ipynb`.
2. Run all cells in order.
3. Upload your code screenshot.
4. Download or copy the generated post.

### Local Setup
```bash
git clone https://github.com/YOUR_USERNAME/daily-code-snapshot-agent.git
cd daily-code-snapshot-agent

python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

brew install tesseract     # macOS
sudo apt install tesseract-ocr   # Linux

export GEMINI_API_KEY="YOUR_KEY"
python run_agent.py --image assets/sample.png

**### Files in This Repository**


**If you find this project useful, please consider starring the repository!**

