```{r}

# Load necessary libraries
library(ggplot2)
library(ggraph)
library(igraph)

# Create a data frame for edges
edges <- data.frame(
  from = c('Root', 'Root', 'Root', 'A', 'A', 'B', 'B', 'C', 'C'),
  to = c('A', 'B', 'C', 'G_A', 'NG_A', 'G_B', 'NG_B', 'G_C', 'NG_C'),
  weight = c(0.7, 0.2, 0.1, 0.1, 0.9, 0.4, 0.6, 0.2, 0.8)
)

# Create a data frame for nodes
nodes <- data.frame(
  name = c('Root', 'A', 'B', 'C', 'G_A', 'NG_A', 'G_B', 'NG_B', 'G_C', 'NG_C'),
  label = c('Managers', 'A: Not Buy (70%)', 'B: Buy (20%)', 'C: Undecided (10%)', 
            'G: Upgrade (10%)', '¬G: Not Upgrade (90%)', 'G: Upgrade (40%)', 
            '¬G: Not Upgrade (60%)', 'G: Upgrade (20%)', '¬G: Not Upgrade (80%)')
)

# Convert to graph object
graph <- graph_from_data_frame(edges, vertices=nodes)

# Plot the graph using ggraph and ggplot2
ggraph(graph, layout = 'tree') + 
  geom_edge_link(aes(edge_label = weight), show.legend = FALSE, arrow = arrow(length = unit(4, 'mm'))) + 
  geom_node_point(color = 'skyblue', size = 5) + 
  geom_node_text(aes(label = label), vjust = 1, hjust = 1) + 
  theme_void()

```