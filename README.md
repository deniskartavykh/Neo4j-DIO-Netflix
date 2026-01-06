query 0

MATCH (n)
UNWIND labels(n) AS Label
RETURN Label, count(*) AS Quantidade
ORDER BY Quantidade DESC;

query 1

MATCH (:User)-[:WATCHED]->(m)-[:IN_GENRE]->(g:Genre)
RETURN g.name AS Genero, count(*) AS Visualizacoes
ORDER BY Visualizacoes DESC
LIMIT 5;

query 2 

MATCH (u:User)-[w:WATCHED]->(m:Movie)
RETURN u, w, m
LIMIT 5;

query 3 - TOP 10 filmes mais populares vs. usuarios únicos

MATCH (u:User)-[:WATCHED]->(content)-[:IN_GENRE]->(g:Genre)
RETURN g.name AS Genero, count(*) AS Total_Visualizacoes, count(DISTINCT u) AS Usuarios_Unicos
ORDER BY Total_Visualizacoes DESC
LIMIT 6;
