# FlyWire

The complete wiring diagram of an adult *Drosophila* brain, from Lin et al., [Nature 2024](https://www.nature.com/articles/s41586-024-07558-y). 127,978 neurons, 2,613,129 directed synaptic connections.

|                        |                       |
| ---------------------- | --------------------- |
| ![](images/schema.png) | ![](images/graph.png) |

## Graph

Neurons are nodes. A synapse between two neurons is a directed edge, weighted by synapse count and annotated with the brain regions and neurotransmitter types involved. Each neuron is classified by cell type, brain hemisphere, signal flow direction and predicted neurotransmitter.

The paper used this connectome to study how the fly brain is organized at a network level — identifying small-world properties, rich-club structure among high-degree neurons and how different sensory pathways (visual, olfactory, mechanosensory) are wired relative to each other.

## Load

**From a dump** (fastest) — download the pre-built dump from S3 and load it directly in Neo4j Desktop, or via the CLI:

```bash
aws s3 cp s3://gds-public-dataset/flywire_graph.dump .
neo4j-admin database load neo4j --from-path=.
```

**From source** — download the raw CSVs and import into any running Neo4j instance:

```bash
git clone https://github.com/murthylab/flywire-network-analysis
cp .env.example .env          # fill in NEO4J_URI, credentials, database
python3 download_graph.py
```
