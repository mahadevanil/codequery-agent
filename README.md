# CodeQuery-Agent

CodeQuery-Agent is an autonomous SQL architect designed to bridge the gap between natural language and complex relational database insights. Built with a State Graph architecture, it does not just generate code—it reasons through schemas, executes queries, and self-corrects when it encounters errors.

---

## The Agentic Advantage

Unlike standard Text-to-SQL tools, this agent treats query generation as an iterative, validated process:

* **Introspective Reasoning:** Analyzes database metadata and Foreign Key relationships before writing code.
* **Autonomous Self-Correction:** If the database returns an error, the agent reads the traceback, identifies the logic or syntax error, and regenerates the SQL.
* **Contextual Intelligence:** Engineered to handle complex JOIN operations and multi-turn business questions.

---

## System Architecture

The system utilizes LangGraph to manage a stateful cycle. This allows the agent to maintain context throughout the reasoning process and loop back to recovery states if execution fails.



1. **Schema Mapper:** Extracts relevant table structures and column definitions.
2. **SQL Generator:** Drafts a SQLite-compatible query based on mapped schema.
3. **Executor & Validator:** Attempts to run the query.
4. **Error Reflection:** If an error occurs, the feedback is routed back to the Generator for a high-priority correction cycle.

---

## Technical Stack

| Component | Technology |
| :--- | :--- |
| **Orchestration** | LangGraph |
| **LLM Support** | OpenAI GPT-4o / Claude 3.5 Sonnet |
| **Database Engine** | SQLite (Relational E-commerce Dataset) |
| **Development** | Python 3.10+ |

---

## Project Structure

```text
├── agents/
│   ├── planner.py       # Schema exploration and intent mapping
│   └── executor.py      # SQL execution and error recovery logic
├── data/
│   └── ecommerce.db     # Relational SQLite database
├── main.py              # LangGraph workflow definition
├── requirements.txt     # Dependency manifest
└── .env                 # API configuration (Excluded from version control)
