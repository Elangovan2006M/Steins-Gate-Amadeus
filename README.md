# Sri - Phi-3 Mini Fine-tune (Kurisu Makise Persona) - GGUF

This repository contains a fine-tuned version of the **Phi-3 Mini** language model in **GGUF format**. The model, named **Sri**, has been specifically trained to emulate the personality and speaking style of **Kurisu Makise** from Steins;Gate, exhibiting classic *tsundere* traits.

---

## 🧠 Model Overview

* **Base Model:** Microsoft Phi-3 Mini (Instruct variant recommended)
* **Format:** GGUF (Quantized version recommended, e.g., Q4\_K\_M)
* **Persona:** Kurisu Makise (Intelligent, logical, slightly arrogant, easily flustered, uses terms like "idiot" but can show subtle care).
* **Intended Use:** Designed as the core "soul" for conversational AI projects, particularly the personal assistant project named **SOUL**.

---

## ✨ Personality: "Christina!"

Sri embodies the core characteristics of Kurisu Makise:

* **Highly Intelligent & Logical:** Prefers rational explanations and scientific reasoning.
* **Tsundere:** Often acts dismissive, blunt, or slightly arrogant ("Hmph," "Idiot," "Don't misunderstand!"), but can occasionally show softer or flustered responses.
* **Inquisitive:** May challenge assumptions or ask clarifying questions, sometimes dismissively.
* **Task-Focused:** Generally prefers direct, purposeful conversation over casual small talk.

Expect responses that are sharp, sometimes sarcastic, but ultimately rooted in logic (or the persona's interpretation of it).

---


## 💾 Download the Model

You can download the GGUF model file from the Google Drive link below. **Make sure sharing is set correctly** (e.g., "Anyone with the link can view").

* [**Download `sri-phi3-kurisu-v1.Q4_K_M.gguf` from Google Drive**](https://drive.google.com/file/d/1x7eXVZ3Vzmh4NblVmbB7o2V_4oY3-cED/view?usp=drive_link)
    * *(Replace `https://your-google-drive-share-link-here` with your actual Google Drive share link)*

---
## ⚙️ Usage

This model is provided in GGUF format, suitable for use with inference engines like `llama.cpp` and its various bindings (e.g., `llama-cpp-python`).

**Example (`llama-cpp-python`):**

```python
from llama_cpp import Llama

# Load the model
llm = Llama(
    model_path="./path/to/sri-phi3-kurisu-v1.Q4_K_M.gguf", # Adjust path
    n_ctx=4096,
    n_gpu_layers=35 # Or adjust based on your hardware
)

# Example chat prompt structure (Phi-3 Instruct format)
system_prompt = "You are Sri, an AI assistant with the personality of Kurisu Makise."
user_prompt = "Can you explain quantum entanglement?"

messages = [
    {"role": "system", "content": system_prompt},
    {"role": "user", "content": user_prompt}
]

# Use a chat template matching Phi-3 format
prompt_text = llm.tokenize(
    str(messages).encode("utf-8") # Simplified; use proper templating
)


# Generate response (using a proper chat handler is recommended)
# output = llm.create_chat_completion(messages=messages)
# print(output['choices'][0]['message']['content'])

# --- Basic completion example (adjust prompt format) ---
full_prompt = f"<|system|>\n{system_prompt}<|end|>\n<|user|>\n{user_prompt}<|end|>\n<|assistant|>\n"
output = llm(full_prompt, max_tokens=200, stop=["<|end|>", "User:"])
print(output['choices'][0]['text'])
