<div align="center">

<!-- ══ HEADER ══ -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0a0a1a,30:1a0533,70:2d1b69,100:0f0c29&height=230&section=header&text=Yash%20Pratap%20Rai&fontSize=58&fontColor=ffffff&fontAlignY=40&desc=ML%20Engineer%20%7C%20LangChain%20%26%20LangGraph%20%7C%20MCP%20%7C%20Agentic%20AI&descAlignY=62&descSize=18&animation=fadeIn" width="100%"/>

<!-- ══ TYPING ANIMATION ══ -->
<a href="https://git.io/typing-svg">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=21&duration=3000&pause=800&color=A78BFA&background=00000000&center=true&vCenter=true&width=760&height=50&lines=Building+Stateful+Agents+with+LangGraph;Connecting+LLMs+to+Tools+via+MCP;Shipping+RAG+Pipelines+with+LangChain;Turning+Data+into+Intelligent+Systems" alt="Typing SVG" />
</a>

<br/><br/>

<!-- ══ STATUS BADGES ══ -->
<img src="https://img.shields.io/badge/Focus-LangGraph%20Agents-7C3AED?style=for-the-badge&labelColor=1a0533" />
<img src="https://img.shields.io/badge/Exploring-Model%20Context%20Protocol-4F46E5?style=for-the-badge&labelColor=1a0533" />
<img src="https://img.shields.io/badge/Status-Open%20to%20Opportunities-22c55e?style=for-the-badge&labelColor=14532d" />

<br/><br/>

<!-- ══ SOCIAL ══ -->
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Yash%20Pratap%20Rai-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yashprataprai)
[![Portfolio](https://img.shields.io/badge/Portfolio-Visit%20Now-7C3AED?style=for-the-badge&logo=vercel&logoColor=white)](https://my-portfolio-kappa-one-29.vercel.app/)
[![Email](https://img.shields.io/badge/Gmail-Contact%20Me-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:yashpratapraiofficial@gmail.com)

![Profile Views](https://komarev.com/ghpvc/?username=yashprataprai&color=7C3AED&style=flat-square&label=Profile+Views)
![GitHub followers](https://img.shields.io/github/followers/yashprataprai?label=Followers&style=flat-square&color=A78BFA)

</div>

---

## 👋 Hey, I'm Yash

I'm an aspiring **Data Scientist and ML Engineer** who loves taking a model from a notebook to something that actually *does* work. These days I'm focused on **agentic AI**: building LLM systems that can reason, call tools, keep state, and recover from mistakes, using **LangChain**, **LangGraph**, and the **Model Context Protocol (MCP)**.

```python
class YashPratapRai:
    role = "Data Scientist & ML Engineer"
    location = "India 🇮🇳"

    core_ml     = ["scikit-learn", "TensorFlow / Keras", "NLP", "Feature Engineering"]
    llm_stack   = ["LangChain", "LangGraph", "HuggingFace", "OpenAI", "Mistral", "Gemini"]
    protocols   = ["Model Context Protocol (MCP)", "Tool / Function Calling"]
    retrieval   = ["RAG", "Embeddings", "Vector Databases"]
    cloud_bi    = ["Azure", "Power BI", "SQL"]

    currently   = "Building stateful multi-step agents and MCP-powered tools"
    philosophy  = "Data in, decisions out. Make the model useful, then make it reliable."

    def open_to(self):
        return ["ML Engineer", "Data Scientist", "GenAI / Agentic AI roles"]
```

---

## 🔭 What I'm Working On

| Area | What I'm doing | Stack |
|:--|:--|:--|
| 🕸️ **LangGraph agents** | Stateful graphs with conditional routing, loops, and human-in-the-loop checkpoints | LangGraph, LangChain |
| 🔌 **MCP servers & clients** | Exposing data and tools to LLMs through a standard protocol instead of one-off integrations | MCP Python SDK |
| 📚 **RAG pipelines** | Chunking, embeddings, retrieval, and evaluation for grounded Q&A | LangChain, FAISS / Chroma |
| 🧪 **Applied ML** | Classical ML + deep learning for prediction and NLP | scikit-learn, TensorFlow |
| 📊 **Analytics** | Dashboards that turn raw data into decisions | Power BI, SQL, Azure |

---

## 🧩 Agent Architecture I Build Towards

```mermaid
flowchart LR
    U([👤 User]) --> R{{🧭 Router}}
    R -->|needs knowledge| RAG[📚 RAG Retriever]
    R -->|needs action| T[🛠️ Tool Executor]
    R -->|simple| L[🧠 LLM]
    RAG --> L
    T <-->|MCP| M[(🔌 MCP Servers<br/>files · DBs · APIs)]
    L --> C{✅ Self-check}
    C -->|retry| R
    C -->|pass| A([💬 Answer])

    style R fill:#4c1d95,stroke:#A78BFA,color:#fff
    style M fill:#1a0533,stroke:#7C3AED,color:#fff
    style L fill:#7C3AED,stroke:#fff,color:#fff
    style C fill:#4c1d95,stroke:#A78BFA,color:#fff
```

---

## 🕸️ LangGraph in Practice

A minimal stateful graph with a retrieve → generate → verify loop:

```python
from typing import TypedDict
from langgraph.graph import StateGraph, END

class State(TypedDict):
    question: str
    context: str
    answer: str
    attempts: int

def retrieve(state: State) -> dict:
    docs = retriever.invoke(state["question"])          # your LangChain retriever
    return {"context": "\n\n".join(d.page_content for d in docs)}

def generate(state: State) -> dict:
    prompt = f"Context:\n{state['context']}\n\nQuestion: {state['question']}"
    return {"answer": llm.invoke(prompt).content,
            "attempts": state.get("attempts", 0) + 1}

def verify(state: State) -> str:
    grounded = grader.invoke({"answer": state["answer"], "context": state["context"]})
    return "done" if grounded or state["attempts"] >= 3 else "retry"

graph = StateGraph(State)
graph.add_node("retrieve", retrieve)
graph.add_node("generate", generate)
graph.set_entry_point("retrieve")
graph.add_edge("retrieve", "generate")
graph.add_conditional_edges("generate", verify, {"done": END, "retry": "retrieve"})

app = graph.compile()
```

---

## 🔌 MCP: One Protocol, Many Tools

I'm exploring MCP as the standard way to plug data and tools into LLM apps. A small analytics server:

```python
from mcp.server.fastmcp import FastMCP
import pandas as pd

mcp = FastMCP("analytics-server")

@mcp.tool()
def describe_dataset(path: str) -> dict:
    """Return row count, columns, and dtypes for a CSV file."""
    df = pd.read_csv(path)
    return {"rows": len(df), "columns": list(df.columns),
            "dtypes": {c: str(t) for c, t in df.dtypes.items()}}

@mcp.tool()
def top_values(path: str, column: str, n: int = 5) -> dict:
    """Most frequent values in a column."""
    return pd.read_csv(path)[column].value_counts().head(n).to_dict()

if __name__ == "__main__":
    mcp.run()
```

Any MCP-compatible client (Claude Desktop, LangGraph agents via MCP adapters, IDEs) can discover and call these tools without custom glue code.

---

## 🛠 Tech Stack

<div align="center">

### 🤖 LLM · Agents · MCP
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-7C3AED?style=for-the-badge&logo=langchain&logoColor=white)
![MCP](https://img.shields.io/badge/MCP-4F46E5?style=for-the-badge&logo=modelcontextprotocol&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)
![Hugging Face](https://img.shields.io/badge/HuggingFace-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)

### 🧪 Machine Learning
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=for-the-badge&logo=keras&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge&logo=python&logoColor=white)

### ☁️ Data · Cloud · BI
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)

### 💻 Secondary
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)

</div>

---

## 🚀 Featured Projects

<div align="center">

| 🎬 Movie Recommendation System | 📝 LSTM Next Word Predictor | 📊 Power BI Dashboards |
|:--|:--|:--|
| Content-based filtering on **45K+ movies** | Deep learning NLP model for sequence prediction | Interactive dashboards for business insights |
| TF-IDF + Cosine Similarity | Stacked LSTM layers | KPI tracking & drill-downs |
| `Python` `scikit-learn` `Pandas` | `TensorFlow` `Keras` `Python` | `Power BI` `SQL` |

</div>

### 🧭 Roadmap: Agentic AI Projects

| Status | Project | Highlights |
|:--:|:--|:--|
| 🔨 | **RAG Q&A system** | LangChain, vector store, retrieval evaluation |
| 🔨 | **Multi-step research agent** | LangGraph state machine, web search tool, citations |
| 🧪 | **MCP analytics server** | Expose datasets and charts as MCP tools |
| 🧪 | **Human-in-the-loop agent** | LangGraph checkpoints, approval steps, memory |
| 📝 | **Agent evaluation harness** | Trace logging, regression tests for prompts and tools |

<sub>🔨 in progress · 🧪 prototyping · 📝 planned</sub>

---

## 🗺️ Learning Path

```mermaid
graph LR
    A[🐍 Python & ML] --> B[🧪 Deep Learning & NLP]
    B --> C[🔗 LangChain & RAG]
    C --> D[🕸️ LangGraph Agents]
    D --> E[🔌 MCP Tools & Servers]
    E --> F[🚀 Production Agents]

    style A fill:#1a0533,stroke:#7C3AED,color:#fff
    style B fill:#1a0533,stroke:#7C3AED,color:#fff
    style C fill:#4c1d95,stroke:#A78BFA,color:#fff
    style D fill:#4c1d95,stroke:#A78BFA,color:#fff
    style E fill:#4c1d95,stroke:#A78BFA,color:#fff
    style F fill:#7C3AED,stroke:#fff,color:#fff
```

---

## 📊 GitHub Stats

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=yashprataprai&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=A78BFA&icon_color=A78BFA&text_color=ffffff&ring_color=7C3AED" height="165"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=yashprataprai&layout=compact&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=A78BFA&text_color=ffffff" height="165"/>

<br/>

<img src="https://github-readme-streak-stats.herokuapp.com?user=yashprataprai&theme=tokyonight&hide_border=true&background=0d1117&ring=7C3AED&fire=A78BFA&currStreakLabel=A78BFA" width="60%"/>

<br/>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=yashprataprai&bg_color=0d1117&color=A78BFA&line=7C3AED&point=ffffff&area=true&hide_border=true" width="90%"/>

</div>

---

## 🤝 Let's Connect

I'm open to **ML Engineer, Data Scientist, and GenAI / Agentic AI** roles, and always happy to talk about LangGraph, MCP, or RAG.

<div align="center">

📫 **[yashpratapraiofficial@gmail.com](mailto:yashpratapraiofficial@gmail.com)** &nbsp;·&nbsp; 💼 **[LinkedIn](https://www.linkedin.com/in/yashprataprai)** &nbsp;·&nbsp; 🌐 **[Portfolio](https://my-portfolio-kappa-one-29.vercel.app/)**

<br/>

<img src="https://quotes-github-readme.vercel.app/api?type=horizontal&theme=tokyonight" width="70%"/>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:24243e,50:302b63,100:0f0c29&height=120&section=footer&text=Thanks%20for%20visiting!%20Star%20if%20you%20like%20it&fontSize=18&fontColor=A78BFA&animation=twinkling" width="100%"/>

</div>
