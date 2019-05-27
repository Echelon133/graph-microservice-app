# graph-microservice-app

Application features:
* read/store directed graphs with non-negative edge weights in a database
* execute Dijkstra algorithm on these graphs and receive information about calculated paths (visited vertexes, weight needed to visit a specific vertex, path to a specific vertex)

## App services scheme 

![Diagram](https://github.com/Echelon133/graph-microservice-app/blob/master/img/microservices-diagram.png)

This application uses a custom graph library written by me. 
That library allows for:
* serialization/deserialization of directed graphs with non-negative edge weights
* execution of the Dijkstra algorithm on these graphs 
* serialization of the Dijkstra algorithm results
* (optional) limiting the number of accepted edges during the deserialization (to prevent abusing the server with execution of the Dijkstra algorithm on too many edges)

## API

| Endpoint                                 | Method     | Request body                    | Description                                      |
|------------------------                  |----------  |-----------------                |-------------                                     |
|/api/graphs/{id}                          | GET        |  ---                            | Get a graph with specified *id*                                  |
|/api/graphs/                              | POST       | JSON representation of a graph  | Validate and save given graph in the database
|/api/graphs/{id}/paths?startFrom={vertex} | POST       |  ---                            | Execute the Dijkstra algorithm on a graph with given *id* (starting from the vertex that has a name equal to the name in parameter *startFrom*)

## Example use

### Graph not found

![NotFound1](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/1NotFound.png)
---
![NotFound2](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/2NotFound.png)

### Graph Validation

#### Missing required nodes

![MissingNode1](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/3MissingNode.png)
---
![MissingNode2](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/4MIssingNode.png)

#### Wrong type of JSON node

![NotArray1](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/5NotArrayNode.png)
---
![NotArray2](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/6NotArrayNode.png)

#### Wrong data type in array

![NotTextual](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/7NotTextual.png)
---
![NotObject](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/8NotObject.png)

#### Edge object missing a field

![NoSource](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/9NoSource.png)
---
![NoDestination](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/10NoDestination.png)
---
![NoWeight](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/11NoWeight.png)

#### Edge object field contains data of wrong type

![SourceNotTextual](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/12SourceNotTextual.png)
---
![DestinationNotTextual](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/13DestinationNotTextual.png)
---
![InvalidWeightType](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/14InvalidWeightType.png)

#### Edge references a vertex that is not declared in 'vertexes'

![InvalidRef](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/15InvalidReference.png)

#### Edge has negative weight

![NegativeWeight](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/16NegativeWeight.png)

#### Valid graph is accepted

![GraphSaved](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/17GraphSaved.png)

#### Optional edge number limit 

![Limit](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/18Limit.png)

#### Accessing already saved graph

![ReadGraph](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/19ReadGraph.png)

#### Checking for required param

![RequiredParam](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/20RequiredParam.png)

#### Dijkstra algorithm execution

![ExecuteAlgorithm](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/21ExecuteAlgorithm.png)

#### Vertex name is checked before algorithm execution

![NoVertexInGraph](https://github.com/Echelon133/graph-microservice-app/blob/master/img/screens/22NoVertexInGraph.png)

