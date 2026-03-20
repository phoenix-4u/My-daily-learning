# Day 2 - 20/03/2026
## Expectation Minimization vs K means
- K means algorithm is deterministic in nature. This creates a problem that if a particular datapoint is equidistant from both the centroids, the point has to be assigned to any one of the centroids randomly. This makes the assignment asymmetric. Expectation Maximization introduces the idea of a probabilistic model instead of a deterministic one. The idea is to assign probability to all the points to be placed at any one of the centroids and then taking an weigted probability for all the clusters for that point. That way the centroid allocation is much more accurate than determinsitic apporach of k means

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
