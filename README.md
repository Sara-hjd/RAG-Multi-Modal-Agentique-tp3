# RAG Multimodal Agentique — TP3

Application RAG (Retrieval-Augmented Generation) **multimodale** et **agentique** qui extrait, indexe et interroge le texte et les images de l'article *Attention Is All You Need*.

```
PDF → PyMuPDF → textes + images → CLIP ViT-B-32 (espace latent commun)
    → ChromaDB (cosinus + métadonnées) → retriever_tool → Agent ReAct (MIND + BODY) avec LangGraph
```

## Étapes (notebook `tp3_rag_multimodal_langgraph.ipynb`)

1. Extraction du contenu multimodal (textes & images)
2. Embeddings CLIP normalisés
3. Indexation dans ChromaDB (identifiant SHA-256, métadonnées)
4. Recherche multimodale par similarité cosinus
5. Transformation du retriever en outil `retriever_tool`
6. Agent ReAct MIND/BODY avec LangGraph
7. Tests et validation

## Installation

Prérequis : [uv](https://docs.astral.sh/uv/) et [Ollama](https://ollama.com/) (LLM local, gratuit).

```bash
uv sync                                   # crée .venv (Python 3.11) et installe les dépendances
uv run python -m ipykernel install --user --name tp3-rag-mm --display-name "TP3 RAG MM (3.11)"
ollama pull qwen3-vl:8b                   # LLM multimodal de l'agent (étape 6)
```

Ouvrir ensuite le notebook, choisir le kernel **TP3 RAG MM (3.11)** puis exécuter toutes les cellules.

Les dossiers `resultats_pdf/` et `chroma_pdf/` sont générés par le notebook.
