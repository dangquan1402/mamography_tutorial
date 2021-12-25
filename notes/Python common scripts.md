---
tags: [Notebook/pytorch]
title: Python common scripts
created: '2021-09-25T04:00:01.388Z'
modified: '2021-09-25T13:26:43.838Z'
---

# Python common scripts

### Average meter



```python
from tqdm.autonotebook import tqdm

class AverageMeter:
    ''' Computes and stores the average and current value '''
    def __init__(self) -> None:
        self.reset()

    def reset(self) -> None:
        self.val = 0.0
        self.avg = 0.0
        self.sum = 0.0
        self.count = 0

    def update(self, val: float, n: int = 1) -> None:
        self.val = val
        self.sum += val * n
        self.count += n
        self.avg = self.sum / self.count
```
### Progress bar

```python

# setup progress bar
tk0 = tqdm(train_loader, total=len(train_loader))
losses = AverageMeter()
avg_score = AverageMeter()

# update averagemeter
losses.update(batch_loss, batch_size)
avg_score.update(batch_score, batch_size)

# update progress bar
tk0.set_postfix(loss=losses.avg, avg_score=avg_score.avg)

```

### Pytorch syntax


```python

outputs = model(inputs) # compute output
loss = criterion(outputs, labels) # compute loss
loss.backward() # backprop
optimizer.step() 
```


### Tensor dataloader

```python
import torch
import numpy as np
from torch.utils.data import TensorDataset, DataLoader

my_x = [np.array([[1.0,2],[3,4]]),np.array([[5.,6],[7,8]])] # a list of numpy arrays
my_y = [np.array([4.]), np.array([2.])] # another list of numpy arrays (targets)

tensor_x = torch.Tensor(my_x) # transform to torch tensor
tensor_y = torch.Tensor(my_y)

my_dataset = TensorDataset(tensor_x,tensor_y) # create your datset
my_dataloader = DataLoader(my_dataset) # create your dataloader
```

### Sample collate function

```python
def collate_valid_fn(batch):
    images, targets = zip(*batch)
    images = torch.stack(images)
    targets = torch.stack(targets).long()
    return {"input": images}, {"target": targets}
```