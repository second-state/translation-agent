- start llamaedge
```bash
wasmedge --dir .:. --nn-preload default:GGML:AUTO:second-state/Llama-3-8B-Instruct-GGUF/Meta-Llama-3-8B-Instruct.Q5_K_M.gguf \
llama-api-server.wasm \
--prompt-template llama-3-chat \
--ctx-size 4096 \
--model-name llama-3-8b
```

- run translation examples
```bash
git clone https://github.com/second-state/translation-agent.git
cd translation-agent
git checkout use_llamaedge

export OPENAI_BASE_URL="http://localhost:8080/v1"
export PYTHONPATH=${PWD}/src

pip install python-dotenv
pip install openai tiktoken icecream langchain_text_splitters

cd examples

python example_script.py
```