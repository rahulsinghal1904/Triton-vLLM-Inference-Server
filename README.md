# Triton vLLM Inference Server

This project sets up an NVIDIA Triton Inference Server using the vLLM backend to serve models like Llama-2-7b.

### Downloading Models

To download the Llama-2-7b model in Hugging Face Transformer format, clone the model repository from Hugging Face. Note that vLLM requires models in the Hugging Face Transformer format (e.g., `Llama-2-7b-hf`).

### Model Configuration

Ensure the model files are structured as follows:

- `model_repository/`
  - `vllm_model/`
    - `1/`
      - `model.json`
    - `Llama-2-7b-hf/`
      - model files...
    - `config.pbtxt`

The configuration files define the model and its settings for Triton. `model.json` provides the path to the model, GPU utilization settings, and other configurations. `config.pbtxt` specifies the backend (`vllm`), instance group settings, and input/output configurations.

### Running Locally with Podman

1. Build the container image for the Triton server.
2. Create a directory to store the model files.
3. Run the server by attaching the model repository and configuring the necessary parameters for GPU and resource utilization.

Alternatively, you can directly run Triton with the model store using `podman` and a custom configuration.

### Running on OpenShift

For OpenShift, deploy the model by syncing the model repository to the running pod. Ensure the pod has access to the Persistent Volume (PV) where the models are stored.

### Test the Server

Once the server is running, you can test the inference server by sending a POST request with a text input and configuration parameters, such as stream and temperature settings, to generate model responses.

### References

- [Triton Inference Server: vLLM Backend](https://github.com/triton-inference-server/vllm_backend)
- [NVIDIA Docs: Triton Inference Server Quickstart](https://docs.nvidia.com/deeplearning/frameworks/triton-inference-server-quickstart)
- [NGC Catalog: Triton Inference Server](https://catalog.ngc.nvidia.com/orgs/nvidia/containers/tritonserver)
- [Hugging Face Model Repository](https://huggingface.co)
