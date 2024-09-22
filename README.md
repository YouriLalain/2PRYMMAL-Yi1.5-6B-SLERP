---
base_model:
- 01-ai/Yi-1.5-6B-Chat
- 01-ai/Yi-1.5-6B
library_name: transformers
tags:
- mergekit
- merge

---
# 2PRYMMAL-Yi1.5-6B-SLERP

This is a merge of pre-trained language models created using [mergekit](https://github.com/cg123/mergekit).

## Merge Details
### Merge Method

This model was merged using the SLERP merge method.

### Models Merged

The following models were included in the merge:
* [01-ai/Yi-1.5-6B-Chat](https://huggingface.co/01-ai/Yi-1.5-6B-Chat)
* [01-ai/Yi-1.5-6B](https://huggingface.co/01-ai/Yi-1.5-6B)

### Configuration

The following YAML configuration was used to produce this model:

```yaml

slices:
  - sources:
      - model: 01-ai/Yi-1.5-6B-Chat
        layer_range: [0, 32]
      - model: 01-ai/Yi-1.5-6B
        layer_range: [0, 32]    
merge_method: slerp
base_model: 01-ai/Yi-1.5-6B-Chat
parameters:
  t:
    - filter: self_attn
      value: [0, 0.25, 0.5, 0.75, 1]
    - filter: mlp
      value: [1, 0.75, 0.5, 0.25, 0]
    - value: 0.5
dtype: bfloat16

```
