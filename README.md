# llms-eval

[![Python](https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white)](https://www.python.org/) [![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/) [![Hugging Face](https://img.shields.io/badge/Hugging%20Face-Inference%20API-FFD21E?logo=huggingface&logoColor=black)](https://huggingface.co/docs/api-inference) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**llms-eval** reúne notebooks práticos, em português do Brasil, sobre avaliação de Large Language Models (LLMs) com [LangChain](https://www.langchain.com/) e a técnica de LLM-as-a-judge.

Os exemplos usam o [Qwen/Qwen3-8B](https://huggingface.co/Qwen/Qwen3-8B) como modelo avaliado e o [Qwen/Qwen3-14B](https://huggingface.co/Qwen/Qwen3-14B) como modelo juiz, ambos via [Hugging Face Inference API](https://huggingface.co/docs/api-inference).

> 📚 Este repositório tem como referência de estudos o [philschmid/evaluate-llms](https://github.com/philschmid/evaluate-llms/).

## Requirements

- Python `>=3.11`
- Conta no [Hugging Face](https://huggingface.co) com token de acesso (`HF_TOKEN`)

### Dependências principais

- `langchain-classic` e `langchain-huggingface` — avaliadores prontos e integração com modelos da Hugging Face
- `huggingface_hub` — cliente (síncrono e assíncrono) da Inference API
- `python-dotenv` — carregamento das variáveis de ambiente
- `tqdm` — barras de progresso nas avaliações em lote

## Installation

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install jupyter nbconvert nbclient ipykernel
```

As demais dependências são instaladas pela primeira célula de cada notebook (`%pip install ...`).

## Usage

Configure as variáveis de ambiente em um arquivo `.env` na raiz do projeto (veja [Configuration](#configuration)) e execute os notebooks no Jupyter/VS Code:
- langchain_for_llm_eval.ipynb
- langchain_rag_eval.ipynb

### Notebooks disponíveis

| Notebook | Descrição |
|---|---|
| [`langchain_for_llm_eval.ipynb`](langchain_for_llm_eval.ipynb) | Avaliação por critérios (concisão, correção com referência e critérios personalizados), avaliação de RAG (`context_qa`) e comparação par a par/pontuação com LangChain |
| [`langchain_rag_eval.ipynb`](langchain_rag_eval.ipynb) | LLM-as-a-judge com métrica aditiva personalizada (contexto, completude e concisão) para avaliar respostas de RAG em lote, de forma assíncrona |

## Configuration

Todas as configurações são feitas via variáveis de ambiente no arquivo `.env`:

| Variável | Descrição | Padrão |
|---|---|---|
| `HF_TOKEN` | Token de acesso da Hugging Face | *(obrigatória)* |
| `HF_MODEL_ID` | Modelo avaliado (gera as respostas) | `Qwen/Qwen3-8B` |
| `HF_MODEL_EVAL_ID` | Modelo juiz (avalia as respostas) | `Qwen/Qwen3-14B` |
| `OPENAI_API_KEY` | Chave da OpenAI (opcional, caso use um GPT como juiz) | *(vazio)* |

## Going further

- Repositório de referência dos estudos: [philschmid/evaluate-llms](https://github.com/philschmid/evaluate-llms/)
- Documentação dos avaliadores do LangChain: [criteria eval chain](https://python.langchain.com/docs/guides/evaluation/string/criteria_eval_chain)
- Modelos utilizados: [Qwen/Qwen3-8B](https://huggingface.co/Qwen/Qwen3-8B) e [Qwen/Qwen3-14B](https://huggingface.co/Qwen/Qwen3-14B)

## License

[MIT](LICENSE)
