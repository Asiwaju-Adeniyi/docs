# The Role of GPUs in Directed Acyclic Graph (DAG) Generation for Proof-of-Work

## Overview
Ethash is the Proof-of-Work algorithm used by Ethereum (prior to its transition to Proof-of-Stake) and other blockchain protocols. A key feature of Ethash is its reliance on a **Directed Acyclic Graph (DAG)**, a large dataset that GPUs use during mining to validate blocks efficiently. The DAG is regenerated every epoch (approximately every 30,000 blocks) and must be stored in a GPU's VRAM.

## Why GPUs Are Crucial
DAG generation and mining operations are memory-intensive rather than compute-intensive. GPUs, with their high memory bandwidth and large VRAM, are better suited for these workloads than CPUs or ASICs. Efficiently generating and storing the DAG on GPUs ensures optimal mining performance and reduces idle computation cycles.

## Key Concepts
- **DAG Generation Process**: The DAG is generated using a seed hash derived from block headers. It is built iteratively to achieve deterministic results across all miners.
- **VRAM Requirements**: As DAG size increases, older GPUs with limited VRAM (e.g., <4GB) become obsolete for mining.
- **Memory Bottlenecks**: Inefficient memory access patterns during DAG generation can lead to significant performance drops.