# Santhosh Dhaipule Chandrakanth

Applied AI engineer. I build the deterministic layer around probabilistic LLMs — local inference, structured-output validation, evaluation harnesses — in Python and C++.

## Found two root-cause bugs in llama.cpp's constrained decoding

Benchmarking small LLMs as structured edit-planners under an 8GB Apple Silicon budget, every model I tested was failing real edit tasks while still scoring 10/10 on JSON-schema validity. Traced it to llama.cpp itself, not the models:

- A grammar requiring an optional key to be written after required keys: 0/69 success with that field present vs. 23/23 without the ordering constraint.
- An empty `{}` JSON schema read as "any object" instead of "no object": 1/31 vs 70/70 depending which side of the bug a test landed on.

Fixed both, added a regression canary and a schema linter, reran the full suite.
→ [harness, raw runs, result hashes](https://github.com/santhoshnumberone/mutation-planner-harness)

## Other work

**License-aware RAG** — fully offline pipeline (LangChain, FAISS, sentence-transformers) answering compliance questions across 20+ open-source licenses on a local Mistral-7B (Q3_K_M). Swept GPU layer offloading (0–64 layers): 3x speedup, no quality loss.
→ [repo](https://github.com/santhoshnumberone/LLM-Power-Search-for-Open-Source-Licensing-Navigator)

**Inference backend benchmark** — llama.cpp vs. ctransformers on matched prompts and token lengths. Metal-accelerated llama.cpp ran ~30% faster.
→ [writeup](https://medium.com/@santhoshnumber1/benchmarking-ctransformers-vs-llama-cpp-local-llm-inference-on-m1-macbook-with-zephyr-mistral-86264805d16b))

**Forgery-detection CNN** — designed from scratch (Inception/ResNet-inspired), trained on 1,800+ authentic/spliced images, ~600 epochs.
→ [repo](https://github.com/santhoshnumberone/Image-Forgery-Detection-) · [training loss]<img width="1419" alt="Screenshot 2025-05-20 at 1 17 08 PM" src="https://github.com/user-attachments/assets/63bba571-51f4-406c-a8ea-aa123195b163" /> · [training accuracy]<img width="1421" alt="Screenshot 2025-05-20 at 1 19 14 PM" src="https://github.com/user-attachments/assets/5a9ecc5c-6a77-4866-bd49-dd346bc323a2" />

## Stack

Python, C++ · PyTorch, TensorFlow, OpenCV · LangChain, FAISS, llama.cpp, GGUF quantization · Docker, AWS

## Contact

Open to Applied AI Engineer / AI Systems Engineer roles — remote, global, or Bangalore onsite.
santhoshnumber1@gmail.com · [LinkedIn](https://www.linkedin.com/in/santhoshnumberone)
