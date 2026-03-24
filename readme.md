# Day 5 - 23/03/2026
## How Agent Skill can be combined
- Agent skills also come in predefined packages.
- One skill that is called skill creator is specifically useful for creating new skills as necessary.
- Multiple custom skills or prebuilt skills can be combined to create a holistic workflow.
- Anthropic has an open source skill library https://github.com/anthropics/skills

<img width="917" height="208" alt="image" src="https://github.com/user-attachments/assets/5a02b5bd-7f73-4950-ac3e-b36a689d926f" />


# Day 4 - 22/03/2026
## How Agent Skill interacts with other GenAI workflow components

- Agent skills can define specific and repeatable workflows that can use sub-agents and MCP tools.
- These can be integrated within the workflow definitions
- Think of tools like hammers, nails, etc. and the skills as the recipe of how to build a bookshelf
- Specific repeatable workflows like code analyzer agent, test case creation agent, etc., can utilize specific skills and MCP servers to execute that specific function

<img width="1905" height="735" alt="image" src="https://github.com/user-attachments/assets/fa482fb7-8430-43f5-8c45-1db73c3b6ead" />

# Day 3 - 21/03/2026
## Why use Agent Skills
- Agent skills are workflow patterns that guide an LLM on what to do
- It is more than a prompt library as it can have instructions for reading reference files, executing scripts, and other styling information
- It is more than an MCP tool calling as it can orchestrate the entire workflow, so that it guides the LLM on what to do without the LLM having to decide based on the doc string on the MCP server
- To avoid clogging the context window, agent skills work on the principle of progressive disclosure. At the start of every skill, which is instruction defined in markdown format, there is a YAML section that contains the skill name and description (sort of like the doc-string of the mcp server), which contains information on what that skill does. For all the skills, only this first part is initially loaded. Based on the user query, the LLM decides which skill is to be used. Once the skill is decided, the LLM then loads the instructions and executes any scripts or MCP server calls. That way, the context window does not overflow even if there are many skills in the skills.md file.
- The folder structure is as follows. The top-level folder is the skill name, which has to match the name definition of the YAML file

<img width="1217" height="524" alt="image" src="https://github.com/user-attachments/assets/724dc148-f9e4-4935-b270-7310211b481c" />

# Day 2 - 20/03/2026
## Expectation Maximization vs K means
- K means algorithm is deterministic in nature. This creates a problem that if a particular datapoint is equidistant from both the centroids, the point has to be assigned to any one of the centroids randomly. This makes the assignment asymmetric. Expectation Maximization introduces the idea of a probabilistic model instead of a deterministic one. The idea is to assign probability to all the points to be placed at any one of the centroids and then taking an weigted probability for all the clusters for that point. That way, the centroid allocation is much more accurate than determinsitic apporach of k means

- <img width="920" height="806" alt="image" src="https://github.com/user-attachments/assets/2c4de131-3dea-499a-9b40-cf809a1427bd" />


# Day 1 - 19/03/2026 
## Graph DB
- Video 8 talks about how to use Langchain to give multishot examples in the prompt and retrieve the correct chunks. The graph DB has to be created in the first place. Creating the cyphers is really difficult, but Langchain's GraphCypherQAChain can create the prompt as well as execute them at one go. Here, though, we have to define schema in the prompt template, since we pass the graph itself as a parameter, we do not have to specify it manually

```python
CYPHER_GENERATION_TEMPLATE = """Task:Generate Cypher statement to query a graph database.
Instructions:
Use only the provided relationship types and properties in the schema.
Do not use any other relationship types or properties that are not provided.
Schema:
{schema}
Note: Do not include any explanations or apologies in your responses.
Do not respond to any questions that might ask anything else than for you to construct a Cypher statement.
Do not include any text except the generated Cypher statement.
Examples: Here are a few examples of generated Cypher statements for particular questions:

# What investment firms are in San Francisco?
MATCH (mgr:Manager)-[:LOCATED_AT]->(mgrAddress:Address)
WHERE mgrAddress.city = 'San Francisco'
RETURN mgr.managerName

# What investment firms are near Santa Clara?
MATCH (address:Address)
WHERE address.city = "Santa Clara"
MATCH (mgr:Manager)-[:LOCATED_AT]->(managerAddress:Address)
WHERE point.distance(address.location,
managerAddress.location) < 10000
RETURN mgr.managerName, mgr.managerAddress

The question is:
{question}"""



CYPHER_GENERATION_PROMPT = PromptTemplate(
input_variables=["schema", "question"],
template=CYPHER_GENERATION_TEMPLATE
)

cypherChain = GraphCypherQAChain.from_llm(
ChatOpenAI(temperature=0),
graph=kg,
verbose=True,
cypher_prompt=CYPHER_GENERATION_PROMPT,
)

prettyCypherChain("What investment firms are near Santa Clara?")
```
