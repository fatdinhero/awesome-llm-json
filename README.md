What is llmjson?
llmjson is a constrained decoding library and Ollama-compatible proxy that guarantees 100% valid JSON from local LLMs on Apple Silicon (MLX).
 
The model physically cannot produce invalid tokens.
Why it belongs on this list:

It fills a gap no other listed library covers: native MLX constrained decoding with drop-in Ollama proxy compatibility. No cloud. No retries. No post-processing.

Feature | llmjson | Outlines | Instructor | lm-format-enforcer |
|---------|---------|----------|------------|-------------------|
| Local / Offline | ✅ | ✅ | ❌ | ✅ |
| Ollama Drop-in proxy | ✅ | ❌ | ❌ | ❌ |
| Apple Silicon MLX | ✅ | ❌ | ❌ | ❌ |
| Zero retries (mathematical guarantee) | ✅ | ✅ | ❌ | ✅ |
| n8n / no-code compatible | ✅ | ❌ | ❌ | ❌ |

**Benchmark:** 80/80 trials passed, zero failures, 95% CI [95.5%, 100%] (Clopper-Pearson).

**Links:** https://github.com/fatdinhero/llmjson



Find the Python Libraries section and add this entry:
llmjson https://github.com/fatdinhero/llmjson

(2024, Apache 2.0, Fatih Dinc / OMNI_GENESIS)
Constrained decoding for local LLMs on Apple Silicon via MLX. Drop-in Ollama proxy — only a port change required. Guarantees 100% schema-valid JSON through VocabScanner + JSONContextTracker (stack FSM) + AND Gate (logit masking). Zero retries. Zero post-processing. n8n compatible.



pip install jsongate



from llmjson import generate

result = generate(
    model_id="mlx-community/Qwen2.5-14B-Instruct-4bit",
    prompt="Profile for Alice, senior engineer",
    schema={"type": "object", "properties": {"name": {"type": "string"}, "age": {"type": "integer"}}}
)
# result.is_valid is always True



Feature
Local / Offline
✅
Ollama Drop-in
✅ (unique in this list)
Apple Silicon MLX
✅
Zero retries
✅
n8n compatible
✅

Benchmark: 80/80 trials, 0 failures across Qwen2.5-14B and Llama-3.1-8B.