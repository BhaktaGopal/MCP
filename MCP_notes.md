**WHAT IS MCP AND HOW DOES IT WORK?**



LLMs are powerful, but they have two major limitations:

* &#x20;Their knowledge is frozen at the time of their training
* &#x20;They can't interact with the outside world

So they can't process real-time data or perform actions like booking a meeting or updating a customer record.

&#x20;

The **Model Context Protocol** (MCP) provides a secure and standardized "language" for LLMs to communicate with external data, applications, and services.

It acts as a bridge, allowing AI to move beyond static knowledge and become a dynamic agent that can retrieve current information and take action, making it more accurate, useful, and automated.



**Understanding the Model Context Protocol**



**MCP** created a standardized, two-way connection for AI applications:-

* Allows LLMs to easily connect with various data sources and tools.
* It builds on existing concepts like tool use and function calling but standardizes them. This reduces the need for custom connections for each new AI model and external system

Hence enables LLMs to work on real-time data which were not included in it's training.



**MCP architecture and components:-**



**MCP HOST:-**

The LLM is contained with the MCP host, an AI application or environment such as an AI-powered IDE or conversational AI.

* User's interaction point, where the MCP host uses the LLM to process requests that may require external data or tools.



**MCP CLIENT:-**

Located inside the MCP Host.

* Helps LLM to communicate with the MCP.
* Translate LLM's requests for MCP and converts the MCP's replies for the LLM.
* Also finds and uses the available MCP servers.



**MCP SERVER:-**

It's an external service that provides context, data, or capabilities to the LLM.

* Connects LLMs to external systems like databases and webservices, translating their responses into a format the LLM can understand.





**TRANSPORT LAYER:-**

Uses JSON-RPC 2.0 messages to communicate between the client and server, mainly through two transport methods:

**Standard input/output(stdio):** Works well for local resources

**Server-sent events(SSE):** Preferred for remote resources, allowing efficient, real-time data streaming.



**HOW DOES THE MCP WORK?**



At the core MCP allows an LLM to request help from external tools to answer a query.



For eg:- the below scenario:-

&#x09;Find the latest sales report in our database and email it to my manager.



**LLM->MCP CLIENT**(search available tools)->**LLM(**Generates a structured request to use these tools.)->**MCP CLIENT(**sends the request to appropriate MCP server)->**MCP SERVER(**receives the request does the necessary then sends back the response to LLM)->**LLM(**provides the final response)

