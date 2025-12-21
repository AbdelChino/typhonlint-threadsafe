# TyphonLint-ThreadSafe
[![PyPI version](https://badge.fury.io/py/typhonlint-threadsafe.svg)](https://badge.fury.io/py/typhonlint-threadsafe)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Downloads](https://static.pepy.tech/badge/typhonlint-threadsafe)](https://pepy.tech/project/typhonlint-threadsafe)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue)](https://www.linkedin.com/in/eugene-evstafev-716669181/)


**Thread Safety Analyzer for JavaScript Code**

A package that analyzes JavaScript code snippets to detect potential race conditions and concurrency conflicts, helping developers ensure thread-safe implementations in multi-threaded environments like Node.js or web workers.

---

## 🚀 Installation

Install via pip:

```bash
pip install typhonlint_threadsafe
```

---

## 📝 Usage

### Basic Usage (Default LLM7)
```python
from typhonlint_threadsafe import typhonlint_threadsafe

# Analyze JavaScript code for thread safety
response = typhonlint_threadsafe(
    user_input="""
    // Example JavaScript code snippet
    let sharedVar = 0;
    function increment() {
        sharedVar++;
    }
    setInterval(increment, 100);
    """
)
print(response)
```

### Custom LLM Integration
You can replace the default LLM (`ChatLLM7`) with any LangChain-compatible model:

#### Using OpenAI
```python
from langchain_openai import ChatOpenAI
from typhonlint_threadsafe import typhonlint_threadsafe

llm = ChatOpenAI()
response = typhonlint_threadsafe(
    user_input="...",  # Your JS code here
    llm=llm
)
```

#### Using Anthropic
```python
from langchain_anthropic import ChatAnthropic
from typhonlint_threadsafe import typhonlint_threadsafe

llm = ChatAnthropic()
response = typhonlint_threadsafe(
    user_input="...",  # Your JS code here
    llm=llm
)
```

#### Using Google Generative AI
```python
from langchain_google_genai import ChatGoogleGenerativeAI
from typhonlint_threadsafe import typhonlint_threadsafe

llm = ChatGoogleGenerativeAI()
response = typhonlint_threadsafe(
    user_input="...",  # Your JS code here
    llm=llm
)
```

---

## 🔧 Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `user_input` | `str` | The JavaScript code snippet to analyze. |
| `api_key` | `Optional[str]` | LLM7 API key (if not provided, falls back to `LLM7_API_KEY` env var). |
| `llm` | `Optional[BaseChatModel]` | Custom LangChain LLM instance (defaults to `ChatLLM7`). |

---

## 🔑 API Key & Rate Limits
- **Default LLM**: Uses `ChatLLM7` from [langchain_llm7](https://pypi.org/project/langchain-llm7/).
- **Free Tier**: Sufficient for most use cases.
- **Custom API Key**: Pass via `api_key` parameter or `LLM7_API_KEY` env var.
- **Get API Key**: [Register at LLM7](https://token.llm7.io/).

---

## 📌 Features
- Detects race conditions in JavaScript code.
- Validates concurrency patterns.
- Structured output for easy integration.
- Supports custom LLMs for flexibility.

---

## 📝 Output
Returns a list of structured assessments indicating:
- Potential thread safety issues.
- Safe concurrency patterns.
- Confirmed correct implementations.

---

## 📂 License
MIT

---

## 📧 Support & Issues
For bugs or feature requests, open an issue on [GitHub](https://github.com/chigwell/typhonlint-threadsafe/issues).

---

## 👤 Author
**Eugene Evstafev** ([@chigwell](https://github.com/chigwell))
📧 [hi@euegne.plus](mailto:hi@euegne.plus)