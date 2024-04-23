# YourselfDataloader
create your own dataloader format data from your own data

This time I put the jupyter notebook code for easy learning and edition, Once you confirm it is helpful, you can write as python lib

PyTorch DataLoader
PyTorch DataLoader is a utility for loading data in PyTorch. It provides an iterator over a dataset, allowing for efficient batching, shuffling, and parallel loading of data, which can significantly accelerate the training process.

Features
Dataset: A container for storing samples and their corresponding labels. Users need to inherit from torch.utils.data.Dataset and implement __getitem__ and __len__ methods for retrieving a single sample and the dataset length, respectively.

DataLoader: An iterator for loading a Dataset. It can be configured with the following parameters:

batch_size: The number of samples per batch
shuffle: Whether to shuffle the data at the start of each epoch
num_workers: The number of subprocesses to use for data loading
drop_last: Whether to drop the last incomplete batch if its size is less than batch_size
Sampler: Defines the strategy for sampling from the dataset. PyTorch provides several common Sampler types such as RandomSampler and SequentialSampler. You can also define your own custom Sampler to meet specific requirements.

Usage
Define your Dataset class:

```Python
from torch.utils.data import Dataset

class MyDataset(Dataset):
    def __init__(self, data, labels):
        self.data = data
        self.labels = labels

    def __getitem__(self, index):
        # Return a single sample and its label
        return self.data[index], self.labels[index]

    def __len__(self):
        return len(self.data)
```

Create a DataLoader instance:
```Python
from torch.utils.data import DataLoader

dataset = MyDataset(data, labels)
dataloader = DataLoader(dataset, batch_size=32, shuffle=True, num_workers=4)
```

Create a DataLoader instance:
```Python
from torch.utils.data import DataLoader

dataset = MyDataset(data, labels)
dataloader = DataLoader(dataset, batch_size=32, shuffle=True, num_workers=4)
```

Iterate over the DataLoader:
```Python
for batch_data, batch_labels in dataloader:
    # Process the batch data
    ...

#or
for i, (imgs, labels) in enumerate(dataloaders['train']):
    # use your dataset by imgs and labels

```
