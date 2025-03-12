#  中文拼写和语法纠错
[**🇨🇳中文**](https://github.com/TW-NLP/ChineseErrorCorrector/blob/main/README.md) 

<div align="center">
  <a href="https://github.com/TW-NLP/ChineseErrorCorrector">
    <img src="images/image_fx_.jpg" alt="Logo" height="156">
  </a>
</div>



-----------------



## 介绍
支持中文拼写和语法错误纠正，并开源拼写和语法错误的增强工具，荣获2024CCL 冠军 🏆，[查看论文](https://aclanthology.org/2024.ccl-3.31/) 。

## 🔥🔥🔥 新闻
[2025/03/12] 为了方便使用，基于AWQ对[twnlp/ChineseErrorCorrector2-7B](https://huggingface.co/twnlp/ChineseErrorCorrector2-7B)进行量化，发布 [twnlp/ChineseErrorCorrector2-7B-AWQ](https://huggingface.co/twnlp/ChineseErrorCorrector2-7B-AWQ)，在单张T4(16G)显卡上即可运行😄, [运行实例]

[2025/03/10] 模型支持多种推理方式，包括 transformers、VLLM、modelscope。

[2025/02/25] 使用200万纠错数据进行多轮迭代训练，发布了[twnlp/ChineseErrorCorrector2-7B](https://huggingface.co/twnlp/ChineseErrorCorrector2-7B)，在 [NaCGEC-2023NLPCC官方评测数据集](https://github.com/masr2000/NaCGEC)上，超越第一名华为17个点，遥遥领先，推荐使用， [技术详情](https://blog.csdn.net/qq_43765734/article/details/145858955)

[2025/02] 为方便部署，发布了[twnlp/ChineseErrorCorrector-1.5B](https://huggingface.co/twnlp/ChineseErrorCorrector-1.5B)

[2025/01] 使用38万开源数据，基于Qwen2.5训练中文拼写纠错模型，支持语似、形似等错误纠正，发布了[twnlp/ChineseErrorCorrector-7B](https://huggingface.co/twnlp/ChineseErrorCorrector-7B)，[twnlp/ChineseErrorCorrector-32B-LORA](https://huggingface.co/twnlp/ChineseErrorCorrector-32B-LORA/tree/main)

[2024/06] v0.1.0版本：开源一键语法错误增强工具，该工具可以进行14种语法错误的增强，不同行业可以根据自己的数据进行错误替换，来训练自己的语法和拼写模型。详见[Tag-v0.1.0](https://github.com/TW-NLP/ChineseErrorCorrector/tree/0.1.0)

## 数据集

| 数据集名称     | 数据链接                                                                                                      | 数据量和类别说明                                                                                                            | 描述          |
|:--------------|:-----------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------|:------------|
| CSC（拼写纠错数据集） |[twnlp/csc_data](https://huggingface.co/datasets/twnlp/csc_data)  | W271K：279,816 条，Medical：39,303 条，Lemon：22,259 条，ECSpell：6,688 条，CSCD：35,001 条 | 中文拼写纠错的数据集 |
| CGC（语法纠错数据集） |[twnlp/cgc_data](https://huggingface.co/datasets/twnlp/cgc_data)  | CGED：20449 条，FCGEC：37354 条，MuCGEC：2467 条，NaSGEC：7568条 | 中文语法纠错的数据集 |
| Lang8+HSK（百万语料-拼写和语法错误混合数据集） |[twnlp/lang8_hsk](https://huggingface.co/datasets/twnlp/lang8_hsk)  | 1568885条 | 中文拼写和语法数据集 |



## 拼写纠错评测
- 评估指标：F1


| Model Name       | Model Link                                                                                                              | Base Model                 | Avg        | SIGHAN-2015(通用) | EC-LAW(法律)| EC-MED(医疗)| EC-ODW(公文)|
|:-----------------|:------------------------------------------------------------------------------------------------------------------------|:---------------------------|:-----------|:------------|:-------|:-------|:--------|
| twnlp/ChineseErrorCorrector-1.5B        | [huggingface](https://huggingface.co/twnlp/ChineseErrorCorrector-1.5B/tree/main)                               | Qwen/Qwen2.5-1.5B-Instruct | 0.459     | 0.346      | 0.517 | 0.433 | 0.540     |
| twnlp/ChineseErrorCorrector-7B        | [huggingface](https://huggingface.co/twnlp/ChineseErrorCorrector-7B/tree/main)                                    | Qwen/Qwen2.5-7B-Instruct | 0.712     | 0.592      | 0.787 | 0.677 | 0.793     |
| twnlp/ChineseErrorCorrector-32B-LORA        | [huggingface](https://huggingface.co/twnlp/ChineseErrorCorrector-32B-LORA/tree/main)                                    | Qwen/Qwen2.5-32B-Instruct |  0.757   |    0.594   | 0.776 |0.794 |   0.864  |

## 文本纠错评测（拼写错误+语法错误）
- 评估工具：ChERRANT  [评测工具](https://github.com/HillZhang1999/MuCGEC)
- 评估数据：[NaCGEC](https://github.com/masr2000/NaCGEC)
- 评估指标：F1-0.5


| Model Name       | Model Link                                                                                                              |    Prec     | Rec | F0.5 |
|:-----------------|:---------------------------------------------------------------|:-----------|:------------|:-------|
|  twnlp/ChineseErrorCorrector2-7B | [huggingface](https://huggingface.co/twnlp/ChineseErrorCorrector2-7B) [modelspose(国内下载)](https://www.modelscope.cn/models/tiannlp/ChineseErrorCorrector2-7B)       |  0.6233     | 0.6228      | 0.6232 |
|  twnlp/ChineseErrorCorrector2-7B-AWQ | [huggingface](https://huggingface.co/twnlp/ChineseErrorCorrector2-7B-AWQ)       |  0.514     | 0.5671      | 0.5238 |
|  HW_TSC_nlpcc2023_cgec(华为) |   未开源     |  0.5095     | 0.3129      | 0.4526 |
| 鱼饼啾啾Plus(北京大学) |   未开源     |  0.5708     | 0.1294      | 0.3394 |
| CUHK_SU(香港中文大学) |  未开源      |  0.3882     | 0.1558      | 0.2990 |
| CGEC++(东南大学) |    未开源    |  0.2414     | 0.0735      | 0.1657 |
| zhao_jia |   未开源     |  0.1719     | 0.1478      | 0.1665 |


## 使用
### transformers 

```shell
pip install transformers
```

```shell
from transformers import AutoModelForCausalLM, AutoTokenizer

model_name = "twnlp/ChineseErrorCorrector2-7B"

model = AutoModelForCausalLM.from_pretrained(
    model_name,
    torch_dtype="auto",
    device_map="auto"
)
tokenizer = AutoTokenizer.from_pretrained(model_name)

prompt = "你是一个文本纠错专家，纠正输入句子中的语法错误，并输出正确的句子，输入句子为："
text_input = "少先队员因该为老人让坐。"
messages = [
    {"role": "user", "content": prompt + text_input}
]
text = tokenizer.apply_chat_template(
    messages,
    tokenize=False,
    add_generation_prompt=True
)
model_inputs = tokenizer([text], return_tensors="pt").to(model.device)

generated_ids = model.generate(
    **model_inputs,
    max_new_tokens=512
)
generated_ids = [
    output_ids[len(input_ids):] for input_ids, output_ids in zip(model_inputs.input_ids, generated_ids)
]

response = tokenizer.batch_decode(generated_ids, skip_special_tokens=True)[0]
print(response)

```

### VLLM

```shell
pip install transformers
pip install vllm==0.3.3
```

```shell
from transformers import AutoTokenizer
from vllm import LLM, SamplingParams

# Initialize the tokenizer
tokenizer = AutoTokenizer.from_pretrained("twnlp/ChineseErrorCorrector2-7B")

# Pass the default decoding hyperparameters of twnlp/ChineseErrorCorrector2-7B
# max_tokens is for the maximum length for generation.
sampling_params = SamplingParams(seed=42,max_tokens=512)

# Input the model name or path. Can be GPTQ or AWQ models.
llm = LLM(model="twnlp/ChineseErrorCorrector2-7B")

# Prepare your prompts
text_input = "少先队员因该为老人让坐。"
messages = [
    {"role": "user", "content": "你是一个文本纠错专家，纠正输入句子中的语法错误，并输出正确的句子，输入句子为："+text_input}
]
text = tokenizer.apply_chat_template(
    messages,
    tokenize=False,
    add_generation_prompt=True
)

# generate outputs
outputs = llm.generate([text], sampling_params)

# Print the outputs.
for output in outputs:
    prompt = output.prompt
    generated_text = output.outputs[0].text
    print(f"Prompt: {prompt!r}, Generated text: {generated_text!r}") 
```


### VLLM 异步推理
```shell
pip install -r requirements.txt
cd ChineseErrorCorrector

python main.py
```

### modelscope 

```shell
pip install modelscope
```

```shell
from modelscope import AutoModelForCausalLM, AutoTokenizer

model_name = "tiannlp/ChineseErrorCorrector2-7B"

model = AutoModelForCausalLM.from_pretrained(
    model_name,
    torch_dtype="auto",
    device_map="auto"
)
tokenizer = AutoTokenizer.from_pretrained(model_name)

prompt = "你是一个文本纠错专家，纠正输入句子中的语法错误，并输出正确的句子，输入句子为："
text_input = "少先队员因该为老人让坐。"
messages = [
    {"role": "user", "content": prompt + text_input}
]
text = tokenizer.apply_chat_template(
    messages,
    tokenize=False,
    add_generation_prompt=True
)
model_inputs = tokenizer([text], return_tensors="pt").to(model.device)

generated_ids = model.generate(
    **model_inputs,
    max_new_tokens=512
)
generated_ids = [
    output_ids[len(input_ids):] for input_ids, output_ids in zip(model_inputs.input_ids, generated_ids)
]

response = tokenizer.batch_decode(generated_ids, skip_special_tokens=True)[0]
print(response)

```

## Citation

If this work is helpful, please kindly cite as:

```bibtex

@inproceedings{wei2024中小学作文语法错误检测,
  title={中小学作文语法错误检测, 病句改写与流畅性评级的自动化方法研究},
  author={Wei, Tian},
  booktitle={Proceedings of the 23rd Chinese National Conference on Computational Linguistics (Volume 3: Evaluations)},
  pages={278--284},
  year={2024}
}
```


## Star History

![Star History Chart](https://api.star-history.com/svg?repos=TW-NLP/ChineseErrorCorrector&type=Date)