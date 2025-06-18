# 🛡️ Anti-Cheat Code Similarity Detector

This project detects AI-generated or plagiarized code by comparing user submissions with a set of AI-generated solutions using:

- 🧠 **GraphCodeBERT** embeddings  
- 🌲 **AST** (Abstract Syntax Tree) parsing via Tree-sitter  
- ✍️ **TF-IDF** vectorization of AST node types  

---

## 🗂️ Project Structure

```
anticheat-model/
├── ai_solutions/         # JSON files containing AI-generated code
├── ast/                  # AST parsing logic and grammars
├── user_submissions/     # User-submitted code for testing
├── utils/                # Embedding & similarity helpers
├── build_languages.py    # Builds Tree-sitter grammars
├── ast_tfidf.py          # TF-IDF similarity on AST tokens
├── check.py              # Main similarity checker script
├── README.md
```

---

## ⚙️ Setup Instructions

### 1. Clone grammar parsers (once)
```bash
git clone https://github.com/tree-sitter/tree-sitter-cpp ast/grammar/tree-sitter-cpp
git clone https://github.com/tree-sitter/tree-sitter-java ast/grammar/tree-sitter-java
git clone https://github.com/tree-sitter/tree-sitter-python ast/grammar/tree-sitter-python
```

### 2. Build the language library
```bash
python3 build_languages.py
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

---

## 🚀 Run the model
```bash
python3 check.py
```

You’ll be prompted to enter:
- User code  
- Language (python/java/cpp)

The system will return:
- GraphCodeBERT similarity  
- AST-TFIDF similarity  
- Final verdict (original or potentially AI-generated)

---

## 📝 Notes
- The current setup supports **Python, C++, and Java**.  
- You can modify `ai_solutions/q1.json` to test with different AI samples.
