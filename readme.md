## Day1 
# Graph DB - 
- Video 8 talks about how to use Langchain to give multishot examples in the prompt and retrieve the correct chunks. The graph db has to be created in the first place. Creating the cyphers is really difficult, but Langchain's GraphCypherQAChain can create the prompt as well as execute them at one go. Here though we have to define schema in the prompt template, since we pass the graph itself as parameter, we do not have to secify it manually

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
