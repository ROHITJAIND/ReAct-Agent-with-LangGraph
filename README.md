# ReAct Agent with LangGraph

 This project implements a student-focused AI assistant using the **ReAct pattern** and the **LangGraph** library.  The agent's core functionality—calculating GPA, looking up due dates, and defining terms—is now powered by a state machine architecture.

-----

### Features

  -  **GPA Calculation**: The agent can compute a GPA from a comma-separated list of grades, such as "A, B+, C".
  -  **Due Date Lookup**: It can retrieve due dates for specific assignments, like "midterm exam" or "final paper".
  -  **Term Definition**: The agent provides definitions for academic terms, including "procrastination" and "plagiarism".
  -  **LangGraph Integration**: The ReAct loop is implemented as a state machine using LangGraph to manage the flow of the agent's actions and observations.
  -  **Extensible**: The project's structure allows for easy expansion by adding new functions as tools.

-----

### Installation

1.  **Clone the repository**:

    ```bash
    git clone https://github.com/your-username/your-repository.git
    cd your-repository
    ```

2.  **Install dependencies**:
    This project requires `LangGraph`, `LangChain`, and `OpenAI`.  You can install them using pip:

    ```bash
    pip install langchain_openai langchain_core langgraph python-dotenv
    ```

3.  **Set up your OpenAI API key**:
     Create a `.env` file in the root directory and add your OpenAI API key.

    ```
    OPENAI_API_KEY="your_api_key_here"
    ```

-----

### Usage

 The agent operates on a graph with two primary nodes: one for the agent's decision-making (`agent_node`) and another for executing tools (`tool_node`).  A conditional edge, managed by the `should_continue` function, directs the flow between these nodes.

 To use the agent, you can pass a question to its stream function. The agent will then run through the graph to provide an answer.

Here's an example:

```python
question_due_date = "When is the midterm exam due?"
print(f"\nUser's question: {question_due_date}\n")
for s in app.stream({"chat_history": [question_due_date]}):
    print(s)
```

 This will show the agent using the `get_due_date` tool to find the answer.

-----

### Summary of Changes

 The updated notebook replaces a manual ReAct simulation with a more robust, LangGraph-based state machine.  This design correctly uses LangGraph's nodes, edges, state, and execution components to create a functional and logically sound agent.
