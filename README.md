# ⚡️ Semgrep-AI - Using Local LLM 🚀

Semgrep-AI is an AI-powered code analysis tool that enhances Semgrep’s static analysis by providing contextual validation of findings using a **local LLM (Large Language Model)**. It helps you gain deeper insights into vulnerabilities, offering explanations, exploitability assessments, confidence ratings, and mitigation tips. 📊🛡️

## 🌟 Key Features

- Validates findings with **code context** (not only just grep and display)for more accurate results 📂
- Outputs detailed reports with **confidence scores** and **exploitability insights** ✅
- Supports custom formatting for results in **CSV** or other file formats 📝 (To-Do)

## ⚙️ Installation & Setup

### 1. Install Ollama and any LLM model

First, ensure you have [Ollama](https://ollama.ai/) installed and any local LLM model of your choice. Ollama makes it easy to run AI models locally. 💻

### 2. Modify `semgrep-ai.py`

Before running Semgrep-AI, modify the following fields in the `semgrep-ai.py` file:

- **Local LLM endpoint**: Point it to the endpoint where your LLM is running.
- **Source code path**: The directory where your project's source code is located.
- **Semgrep output path**: The path where Semgrep will store its analysis output in `.sarif` format.

### 3. Run Semgrep with SARIF Output

Execute Semgrep on your codebase and generate the output in SARIF format. You can do this by adding the `--sarif` flag when running Semgrep:

```bash
semgrep --config <your-semgrep-config> --sarif > output.sarif
```

## 4. Run `semgrep-ai.py`

After Semgrep produces the SARIF output, run `semgrep-ai.py`:

```
python3 semgrep-ai.py
```

## 🔍 What does semgrep-ai do?

### Extracts Vulnerability Information:
- The script extracts the vulnerable code snippet, file path, and line number from the `output.sarif` file.

### Contextual Analysis:
- It uses the file path to locate the vulnerable file in the source code, gathering additional context around the vulnerable snippet.

### LLM-powered Analysis:
- The vulnerable code snippet, file path, and line number are sent to the local LLM for further analysis.
- The model analyzes the context and provides detailed insights based on a structured prompt.

## 💡 What are the insights provided?

The LLM provides insights in the following format:

- **Vulnerability Name**: The type of vulnerability found (e.g., XSS, SQL Injection).
- **Vulnerable Code**: The code snippet that is identified as vulnerable.
- **How it can be Exploited**: A description of how an attacker could exploit the vulnerability.
- **Rate My Confidence**: A confidence score indicating how sure the AI is about the exploitability of the vulnerability.
- **Other Comments**: Suggestions for mitigation or other important comments.

## 📊 Output

- The results from the LLM analysis are saved in a CSV file, making it easy to integrate with other tools or workflows. 


Feel free to adapt the result format as needed! The output can be converted into any file format and schema that suits your project.

### Project Inspiration
You can find the project repository at [ai-secure-code-review](https://github.com/247arjun/ai-secure-code-review/tree/main) by [@247arjun](https://github.com/247arjun) 
