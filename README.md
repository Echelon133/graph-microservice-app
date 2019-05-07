# graph-microservice-app

Application features:
* read/store directed graphs with non-negative edge weights in a database
* execute Dijkstra algorithm on these graphs and receive information about calculated paths (visited vertexes, weight needed to visit a specific vertex, path to a specific vertex)

This application uses a custom graph library written by me. 
That library allows for:
* serialization/deserialization of directed graphs with non-negative edge weights
* execution of the Dijkstra algorithm on these graphs 
* serialization of the Dijkstra algorithm results
* (optional) limiting the number of accepted edges during the deserialization (to prevent abusing the server with execution of the Dijkstra algorithm on too many edges)

