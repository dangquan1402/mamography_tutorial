---
tags: [Notebook/kaggle]
title: Kernels and previous solutions
created: '2021-09-26T23:36:52.650Z'
modified: '2021-09-27T09:15:03.138Z'
---

# Kernels and previous solutions


## Dataset
- [External data](https://www.kaggle.com/rhtsingh/external-data-mlqa-xquad-preprocessing)
- [Fine tune](https://www.kaggle.com/rhtsingh/chaii-qa-5-fold-xlmroberta-torch-fit)

## Some new terminology

- group learning rate decay
- simple attention head
- validation step policy 
- google quest #1 solution
- separate lr for head


```python
def create_optimizer(model):
    named_parameters = list(model.named_parameters())    
    
    roberta_parameters = named_parameters[:197]    
    attention_parameters = named_parameters[199:203]
    regressor_parameters = named_parameters[203:]
        
    attention_group = [params for (name, params) in attention_parameters]
    regressor_group = [params for (name, params) in regressor_parameters]

    parameters = []
    parameters.append({"params": attention_group})
    parameters.append({"params": regressor_group})

    for layer_num, (name, params) in enumerate(roberta_parameters):
        weight_decay = 0.0 if "bias" in name else 0.01

        lr = 2e-5

        if layer_num >= 69:        
            lr = 5e-5

        if layer_num >= 133:
            lr = 1e-4

        parameters.append({"params": params,
                           "weight_decay": weight_decay,
                           "lr": lr})

    return AdamW(parameters)

```

- [simple solution](https://www.kaggle.com/potatoc5/final-sub)



