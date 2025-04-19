## Agentic RAG

Following this lanngraph [tutorial](https://langchain-ai.github.io/langgraph/tutorials/rag/langgraph_agentic_rag/#nodes-and-edges) to create a RAG agent.

## The issues that the above tutorial had:
1. After the rewrite node, the agent node did not trigger any more tool calls and thus ended the flow after the 1st iteration.
2. The agent node also ended the flow without generating any response for the updated question

## The solution:
1. Strict the rewrite node to a structured output and use that to form a new Message with HumanMessage and then re route to the agent node
2. Doing so, the agent node will be able to trigger tool calls iteratively till the retrieve node finds an appropriate doc chuncks by reformatting the question