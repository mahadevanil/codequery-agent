# CodeQuery-Agent

**CodeQuery-Agent** is an autonomous SQL architect designed to bridge the gap between natural language and complex relational database insights. Built with a **State Graph** architecture, it doesn't just generate code—it reasons through schemas, executes queries, and **self-corrects** when it encounters errors.

---

## The Agentic Advantage

Unlike standard Text-to-SQL tools, this agent treats query generation as an iterative process:

* **Introspective Reasoning:** Analyzes database metadata and Foreign Key relationships before writing code.
* **Autonomous Self-Correction:** If the database returns an error, the agent reads the traceback and regenerates the SQL to fix the issue.
* **Contextual Intelligence:** Built to handle complex JOINs and multi-turn business questions.

---

## How it Works (The Workflow)

The system uses **LangGraph** to manage a stateful cycle:
1.  **Schema Mapper:** Extracts relevant table structures.
2.  **SQL Generator:** Drafts a SQLite-compatible query.
3.  **Executor & Validator:** Runs the query. If it fails, the error log is fed back to the Generator for a high-priority "Reflect & Fix" iteration.

---

## Tech Stack

* **Orchestration:** [LangGraph](https://github.com/langchain-ai/langgraph)
* **Framework:** [LangChain](https://github.com/langchain-ai/langchain)
* **LLM:** OpenAI GPT-4o / Claude 3.5 Sonnet
* **Database:** SQLite (Relational E-commerce Dataset)
* **Frontend:** Flutter (Coming in Week 3)

---

## Project Structure

```text
├── agents/
│   ├── planner.py      # Schema exploration logic
│   └── executor.py     # SQL execution & error handling
├── data/
│   └── ecommerce.db    # Relational SQLite database
├── main.py             # LangGraph workflow definition
├── requirements.txt    # Dependencies
└── .env                # API Keys (Git-ignored)
