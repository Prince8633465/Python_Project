# Lambton College Policies Chatbot

## Steps to run

1. Install the python dependencies

```
pip3 install -r requirements.txt
```

2. Run the following command to start the chatbot

```
streamlit run chatbot.py
```

3. Open the browser and navigate to the following URL

```
http://localhost:8501
```

**NOTE**: The first run will take sometime since the model needs to be downloaded from the URL which is around `3GB` size. Subsequent runs will be faster since it will just load the models.

## Experimenting with multiple models

The chatbot can be configured to use different models by changing the `MODEL_URL` in the `chatbot.py` file.

```python
MODEL_URL = "https://huggingface.co/TheBloke/Llama-2-7B-chat-GGUF/resolve/main/llama-2-7b-chat.Q3_K_L.gguf"
```

The above URL is the model that is currently being used. To use a different model, change the URL to the desired model.

- Make sure that the model you replace is a quantized model as the chatbot is currently configured to use quantized models.
- Also it needs to a chat / instruct model from `llama` family.

## Alternate Models**

**Llama 2 7B Chat Models**

| Name | Quant method | Bits | Size | Max RAM required | Use case |
|------|--------------|------|------|------------------|----------|
| llama-2-7b-chat.Q2_K.gguf | Q2_K | 2 | 2.83 GB | 5.33 GB | smallest, significant quality loss - not recommended for most purposes |
| llama-2-7b-chat.Q3_K_S.gguf | Q3_K_S | 3 | 2.95 GB | 5.45 GB | very small, high quality loss |
| llama-2-7b-chat.Q3_K_M.gguf | Q3_K_M | 3 | 3.30 GB | 5.80 GB | very small, high quality loss |
| llama-2-7b-chat.Q3_K_L.gguf | Q3_K_L | 3 | 3.60 GB | 6.10 GB | small, substantial quality loss |
| llama-2-7b-chat.Q4_0.gguf | Q4_0 | 4 | 3.83 GB | 6.33 GB | legacy; small, very high quality loss - prefer using Q3_K_M |
| llama-2-7b-chat.Q4_K_S.gguf | Q4_K_S | 4 | 3.86 GB | 6.36 GB | small, greater quality loss |
| llama-2-7b-chat.Q4_K_M.gguf | Q4_K_M | 4 | 4.08 GB | 6.58 GB | medium, balanced quality - recommended |
| llama-2-7b-chat.Q5_0.gguf | Q5_0 | 5 | 4.65 GB | 7.15 GB | legacy; medium, balanced quality - prefer using Q4_K_M |
| llama-2-7b-chat.Q5_K_S.gguf | Q5_K_S | 5 | 4.65 GB | 7.15 GB | large, low quality loss - recommended |
| llama-2-7b-chat.Q5_K_M.gguf | Q5_K_M | 5 | 4.78 GB | 7.28 GB | large, very low quality loss - recommended |
| llama-2-7b-chat.Q6_K.gguf | Q6_K | 6 | 5.53 GB | 8.03 GB | very large, extremely low quality loss |
| llama-2-7b-chat.Q8_0.gguf | Q8_0 | 8 | 7.16 GB | 9.66 GB | very large, extremely low quality loss - not recommended |

**Llama 2 13B Chat Models**

| Name | Quant method | Bits | Size | Max RAM required | Use case |
|------|--------------|------|------|------------------|----------|
| llama-2-13b-chat.Q2_K.gguf | Q2_K | 2 | 5.43 GB | 7.93 GB | smallest, significant quality loss - not recommended for most purposes |
| llama-2-13b-chat.Q3_K_S.gguf | Q3_K_S | 3 | 5.66 GB | 8.16 GB | very small, high quality loss |
| llama-2-13b-chat.Q3_K_M.gguf | Q3_K_M | 3 | 6.34 GB | 8.84 GB | very small, high quality loss |
| llama-2-13b-chat.Q3_K_L.gguf | Q3_K_L | 3 | 6.93 GB | 9.43 GB | small, substantial quality loss |
| llama-2-13b-chat.Q4_0.gguf | Q4_0 | 4 | 7.37 GB | 9.87 GB | legacy; small, very high quality loss - prefer using Q3_K_M |
| llama-2-13b-chat.Q4_K_S.gguf | Q4_K_S | 4 | 7.41 GB | 9.91 GB | small, greater quality loss |
| llama-2-13b-chat.Q4_K_M.gguf | Q4_K_M | 4 | 7.87 GB | 10.37 GB | medium, balanced quality - recommended |
| llama-2-13b-chat.Q5_0.gguf | Q5_0 | 5 | 8.97 GB | 11.47 GB | legacy; medium, balanced quality - prefer using Q4_K_M |
| llama-2-13b-chat.Q5_K_S.gguf | Q5_K_S | 5 | 8.97 GB | 11.47 GB | large, low quality loss - recommended |
| llama-2-13b-chat.Q5_K_M.gguf | Q5_K_M | 5 | 9.23 GB | 11.73 GB | large, very low quality loss - recommended |
| llama-2-13b-chat.Q6_K.gguf | Q6_K | 6 | 10.68 GB | 13.18 GB | very large, extremely low quality loss |
| llama-2-13b-chat.Q8_0.gguf | Q8_0 | 8 | 13.83 GB | 16.33 GB | very large, extremely low quality loss - not recommended |

## Model

The model used in this chatbot is [llama-2-7b-chat.Q3_K_L.gguf](https://huggingface.co/TheBloke/Llama-2-7B-chat-GGUF/resolve/main/llama-2-7b-chat.Q3_K_L.gguf) which is a 7B parameter model trained on the Llama dataset.

## Chatbot

The chatbot is built using the `streamlit` library. The chatbot is a simple chatbot that can be used to ask questions related to the policies of Lambton College. The extracted data is stored in the `data` folder. The chatbot currently uses the `llama-2-7b-chat.Q3_K_L.gguf` model to generate responses. The implementation of the chatbot is based on **Retrival Augmented Generation (RAG)**.

## Benchmarks

Following benchmark on the following mentioned GPU and model

**model**: [llama-2-7b-chat.Q3_K_L.gguf](https://huggingface.co/TheBloke/Llama-2-7B-chat-GGUF/resolve/main/llama-2-7b-chat.Q3_K_L.gguf)
**GPU**: Nvidia T4 (Standard) - 16GB VRAM

**Brief Answer**

Brief replies are responded in few seconds.

```
llama_print_timings:        load time =   18652.85 ms
llama_print_timings:      sample time =      31.90 ms /    59 runs   (    0.54 ms per token,  1849.53 tokens per second)
llama_print_timings: prompt eval time =   22966.91 ms /   615 tokens (   37.34 ms per token,    26.78 tokens per second)
llama_print_timings:        eval time =    6174.52 ms /    58 runs   (  106.46 ms per token,     9.39 tokens per second)
llama_print_timings:       total time =   29489.61 ms /   673 tokens
```

```
llama_print_timings:        load time =    5828.63 ms
llama_print_timings:      sample time =      25.90 ms /    49 runs   (    0.53 ms per token,  1891.67 tokens per second)
llama_print_timings: prompt eval time =    5828.34 ms /   167 tokens (   34.90 ms per token,    28.65 tokens per second)
llama_print_timings:        eval time =    4821.18 ms /    48 runs   (  100.44 ms per token,     9.96 tokens per second)
llama_print_timings:       total time =   10898.16 ms /   215 tokens
```
#   P y t h o n _ P r o j e c t  
 