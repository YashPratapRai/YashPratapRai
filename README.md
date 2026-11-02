<div align="center">

<!-- ══ HERO HEADER ══ -->
<img src="https://capsule-render.vercel.app/api?type=venom&color=0:0a0a1a,35:1a0533,70:4c1d95,100:7c3aed&height=260&section=header&text=Yash%20Pratap%20Rai&fontSize=62&fontColor=ffffff&fontAlignY=38&desc=ML%20Engineer%20%E2%80%A2%20LangChain%20%E2%80%A2%20LangGraph%20%E2%80%A2%20MCP%20%E2%80%A2%20Agentic%20AI&descSize=18&descAlignY=60&animation=fadeIn" width="100%"/>

<a href="https://git.io/typing-svg">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=22&duration=2800&pause=700&color=C4B5FD&background=00000000&center=true&vCenter=true&width=780&height=55&lines=Building+stateful+agents+with+LangGraph;Wiring+LLMs+to+real+tools+through+MCP;Shipping+grounded+RAG+pipelines+with+LangChain;Turning+data+into+intelligent+systems" alt="Typing SVG" />
</a>

<br/>

<img src="https://img.shields.io/badge/LangGraph-Stateful%20Agents-7C3AED?style=for-the-badge&labelColor=1a0533" />
<img src="https://img.shields.io/badge/MCP-Tool%20Integration-4F46E5?style=for-the-badge&labelColor=1a0533" />
<img src="https://img.shields.io/badge/RAG-Grounded%20LLMs-A78BFA?style=for-the-badge&labelColor=1a0533" />
<img src="https://img.shields.io/badge/Open%20to-Opportunities-22c55e?style=for-the-badge&labelColor=14532d" />

<br/><br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yashprataprai)
[![Portfolio](https://img.shields.io/badge/Portfolio-Visit-7C3AED?style=for-the-badge&logo=vercel&logoColor=white)](https://my-portfolio-kappa-one-29.vercel.app/)
[![Email](https://img.shields.io/badge/Email-Say%20Hi-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:yashpratapraiofficial@gmail.com)

![Profile Views](https://komarev.com/ghpvc/?username=yashprataprai&color=7C3AED&style=flat-square&label=Profile+Views)
![Followers](https://img.shields.io/github/followers/yashprataprai?label=Followers&style=flat-square&color=A78BFA)

</div>

<br/>

<!-- ══ ABOUT ══ -->
<div align="center">

## ✨ About Me

</div>

<table align="center">
<tr>
<td width="55%" valign="top">

I'm an aspiring **Data Scientist and ML Engineer** who likes taking a model from a notebook to something that actually does work.

Right now I'm going deep on **agentic AI**: LLM systems that reason, call tools, keep state, and recover from mistakes, built with **LangChain**, **LangGraph**, and the **Model Context Protocol (MCP)**.

- 🔭 Building stateful multi-step agents with **LangGraph**
- 🔌 Exposing data and tools to LLMs through **MCP**
- 📚 Designing **RAG** pipelines with retrieval evaluation
- 🧪 Applying **classical ML + deep learning** to NLP and prediction
- 🎯 Open to **ML Engineer / Data Scientist / GenAI** roles

</td>
<td width="45%" valign="top">

```python
class Yash:
    role = "ML Engineer"
    location = "India 🇮🇳"

    stack = [
        "LangChain", "LangGraph",
        "MCP", "RAG",
        "scikit-learn", "TensorFlow",
    ]

    focus = "Agents that reason, plan & act"

    def mission(self):
        return "Make models useful, then reliable."
```

</td>
</tr>
</table>

<br/>

<!-- ══ FOCUS CARDS ══ -->
<div align="center">

## 🎯 What I Work On

| 🕸️ LangGraph | 🔗 LangChain | 🔌 MCP | 🧪 Machine Learning |
|:---:|:---:|:---:|:---:|
| Stateful agent graphs | RAG pipelines | MCP servers & clients | scikit-learn models |
| Conditional routing | Retrievers & chains | Tool discovery | Deep learning with Keras |
| Loops & retries | Prompt templates | Standard tool interface | NLP & recommenders |
| Human-in-the-loop | Output parsing | Data and API access | Evaluation & tuning |

</div>

---

<!-- ══ ARCHITECTURE ══ -->
<div align="center">

## 🧩 The Kind of Agent I Build

</div>

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

    style U fill:#1a0533,stroke:#7C3AED,color:#fff
    style R fill:#4c1d95,stroke:#A78BFA,color:#fff
    style RAG fill:#1a0533,stroke:#7C3AED,color:#fff
    style T fill:#1a0533,stroke:#7C3AED,color:#fff
    style M fill:#1a0533,stroke:#A78BFA,color:#fff
    style L fill:#7C3AED,stroke:#fff,color:#fff
    style C fill:#4c1d95,stroke:#A78BFA,color:#fff
    style A fill:#22c55e,stroke:#fff,color:#fff
```

---

<!-- ══ CODE SHOWCASE ══ -->
<div align="center">

## 💻 Code I'm Writing

</div>

<details open>
<summary><b>🕸️ LangGraph: retrieve → generate → verify loop</b></summary>

<br/>

```python
from typing import TypedDict
from langgraph.graph import StateGraph, END

class State(TypedDict):
    question: str
    context: str
    answer: str
    attempts: int

def retrieve(state: State) -> dict:
    docs = retriever.invoke(state["question"])          # LangChain retriever
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

</details>

<details>
<summary><b>🔌 MCP: a small analytics server</b></summary>

<br/>

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

Any MCP-compatible client can discover and call these tools without custom glue code.

</details>

---

<!-- ══ TECH STACK ══ -->
<div align="center">

## 🛠 Tech Stack

<img src="https://skillicons.dev/icons?i=py,tensorflow,sklearn,pandas,numpy,fastapi,postgres,powerbi,docker,git,github,vscode&theme=dark&perline=12" />

<br/><br/>

![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-7C3AED?style=for-the-badge&logo=langchain&logoColor=white)
![MCP](https://img.shields.io/badge/MCP-4F46E5?style=for-the-badge&logo=modelcontextprotocol&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)
![Hugging Face](https://img.shields.io/badge/HuggingFace-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)
![Keras](https://img.shields.io/badge/Keras-D00000?style=for-the-badge&logo=keras&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge&logo=python&logoColor=white)

</div>

---

<!-- ══ PROJECTS ══ -->
<div align="center">

## 🚀 Featured Projects

| 🎬 Movie Recommendation System | 📝 LSTM Next Word Predictor | 📊 Power BI Dashboards |
|:--|:--|:--|
| Content-based filtering on **45K+ movies** | Deep learning NLP model for sequence prediction | Interactive dashboards for business insights |
| TF-IDF + Cosine Similarity | Stacked LSTM layers | KPI tracking & drill-downs |
| `Python` `scikit-learn` `Pandas` | `TensorFlow` `Keras` `Python` | `Power BI` `SQL` |

</div>

<br/>

<div align="center">

### 🧭 Agentic AI Roadmap

| Status | Project | Highlights |
|:--:|:--|:--|
| 🔨 | **RAG Q&A system** | LangChain, vector store, retrieval evaluation |
| 🔨 | **Multi-step research agent** | LangGraph state machine, search tool, citations |
| 🧪 | **MCP analytics server** | Datasets and charts exposed as MCP tools |
| 🧪 | **Human-in-the-loop agent** | LangGraph checkpoints, approval steps, memory |
| 📝 | **Agent evaluation harness** | Trace logging, regression tests for prompts and tools |

<sub>🔨 in progress &nbsp;·&nbsp; 🧪 prototyping &nbsp;·&nbsp; 📝 planned</sub>

</div>

---

<!-- ══ LEARNING PATH ══ -->
<div align="center">

## 🗺️ Learning Path

</div>

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

<!-- ══ STATS ══ -->
<div align="center">

## 📊 GitHub Stats

<img src="https://github-readme-stats.vercel.app/api?username=yashprataprai&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=A78BFA&icon_color=A78BFA&text_color=ffffff&ring_color=7C3AED" height="170"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=yashprataprai&layout=compact&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=A78BFA&text_color=ffffff" height="170"/>

<br/>

<img src="https://github-readme-streak-stats.herokuapp.com?user=yashprataprai&theme=tokyonight&hide_border=true&background=0d1117&ring=7C3AED&fire=A78BFA&currStreakLabel=A78BFA" width="62%"/>

<br/>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=yashprataprai&bg_color=0d1117&color=A78BFA&line=7C3AED&point=ffffff&area=true&hide_border=true" width="92%"/>

</div>

---

<!-- ══ CONTACT ══ -->
<div align="center">

## 🤝 Let's Build Something

I'm open to **ML Engineer, Data Scientist, and GenAI / Agentic AI** roles, and always up for a chat about LangGraph, MCP, or RAG.

<br/>

📫 [yashpratapraiofficial@gmail.com](mailto:yashpratapraiofficial@gmail.com) &nbsp;•&nbsp; 💼 [LinkedIn](https://www.linkedin.com/in/yashprataprai) &nbsp;•&nbsp; 🌐 [Portfolio](https://my-portfolio-kappa-one-29.vercel.app/)

<br/>

<img src="https://quotes-github-readme.vercel.app/api?type=horizontal&theme=tokyonight" width="70%"/>

<img src="https://capsule-render.vercel.app/api?type=venom&color=0:7c3aed,50:4c1d95,100:0a0a1a&height=120&section=footer&text=Thanks%20for%20visiting%20%E2%AD%90&fontSize=20&fontColor=ffffff&animation=twinkling" width="100%"/>

</div>
