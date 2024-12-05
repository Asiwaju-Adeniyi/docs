# Smart Contract APIs for Tokenizing GPU Compute Power

## API Overview

### Resource Certification API
- **Function**: `benchmark_gpu`
- **Parameters**:
  - `gpu_specs`: GPU hardware specifications (VRAM, CUDA cores, clock speed).
  - `workload`: Standardized benchmarking workload (e.g., AI model training).
  - `cert_hash`: Output hash certifying the GPU's performance.
- **Description**: Runs a benchmarking process to validate and tokenize the GPU's computational power.

### Token Minting API
- **Function**: `mint_gpu_token`
- **Parameters**:
  - `gpu_id`: Certified GPU identifier.
  - `benchmark_score`: Performance metric tied to the token's value.
  - `owner_address`: Blockchain address of the GPU owner.
- **Description**: Mints a tradable token representing the GPU's computational power.

### Marketplace API
- **Function**: `list_token_for_rent`
- **Parameters**:
  - `token_id`: Token identifier.
  - `price_per_hour`: Rental cost in cryptocurrency.
  - `availability`: Time slots when the GPU is available for use.
- **Description**: Lists a GPU token on the marketplace for renting.

### Resource Utilization API
- **Function**: `allocate_gpu`
- **Parameters**:
  - `token_id`: Token identifier for the rented GPU.
  - `job_payload`: Compute job specification (e.g., AI training script).
- **Description**: Allocates GPU power for a specific workload using the rented token.