# LSEC-GNN

The repository contains the details about our paper **[Leveraging Tripartite Interaction Information from Live Stream E-Commerce for Improving Product Recommendation](https://arxiv.org/abs/2106.03415)** (KDD 2021).

## Requirements

- Linux-based OS
- Python 3.6+

## Get started

### Clone the project

```bash
git clone https://github.com/yusanshi/LSEC-GNN && cd LSEC-GNN
```

### Install the package

Note this repository contains no model code. Instead we organized our code into a separate Python package called [RecHub](https://github.com/yusanshi/RecHub/). It is a general package for recommendation featuring GNN training especially heterogeneous graph. Refer to its repository for the details.

```bash
pip install rechub
```

If there are any problems with later commands, try to install this specific version ([PyPI](https://pypi.org/project/rechub/TODO/), [GitHub](https://github.com/yusanshi/RecHub/tree/TODO-hash)):

```bash
pip install rechub==TODO
```

### Download the dataset

```bash
mkdir data && cd data
wget https://github.com/yusanshi/LSEC-GNN/files/6520753/LSEC-Small-aa.dummy.gz \
 https://github.com/yusanshi/LSEC-GNN/files/6520754/LSEC-Small-ab.dummy.gz \
 https://github.com/yusanshi/LSEC-GNN/files/6520757/LSEC-Small-ac.dummy.gz \
 https://github.com/yusanshi/LSEC-GNN/files/6520760/LSEC-Small-ad.dummy.gz
cat LSEC-Small-* | tar -xzvf -
```

### Train

![table](https://user-images.githubusercontent.com/36265606/119290511-33271580-bc7f-11eb-84bc-e485fd4ab93b.png)

Each line of commands corresponds to a method in the above table (taken from the paper).

```bash
# In the project root directory
python -m rechub.train --model_name NCF --dataset_path ./data/LSEC-Small --metadata_path ./metadata/LSEC.json --edge_choice 0 --training_task_choice 0 --evaluation_task_choice 0
python -m rechub.train --model_name GCN --dataset_path ./data/LSEC-Small --metadata_path ./metadata/LSEC.json --edge_choice 0 --training_task_choice 0 --evaluation_task_choice 0
python -m rechub.train --model_name LightGCN --dataset_path ./data/LSEC-Small --metadata_path ./metadata/LSEC.json --edge_choice 0 --training_task_choice 0 --evaluation_task_choice 0
python -m rechub.train --model_name GAT --dataset_path ./data/LSEC-Small --metadata_path ./metadata/LSEC.json --edge_choice 0 --training_task_choice 0 --evaluation_task_choice 0
python -m rechub.train --model_name HET-GCN --dataset_path ./data/LSEC-Small --metadata_path ./metadata/LSEC.json --edge_choice 0 1 2 --training_task_choice 0 1 --evaluation_task_choice 0
python -m rechub.train --model_name HET-LightGCN --dataset_path ./data/LSEC-Small --metadata_path ./metadata/LSEC.json --edge_choice 0 1 2 --training_task_choice 0 1 --evaluation_task_choice 0
python -m rechub.train --model_name HET-GAT --dataset_path ./data/LSEC-Small --metadata_path ./metadata/LSEC.json --edge_choice 0 1 2 --training_task_choice 0 1 --evaluation_task_choice 0
```

You can visualize metrics with TensorBoard.

```bash
tensorboard --logdir runs
```

> Tip: by adding `REMARK` environment variable, you can make the runs name in TensorBoard more meaningful. For example, `REMARK=lr-0.001 python -m rechub.train ...`.

### Test

You can run the training commands with parameter `--save_checkpoint True` and use the saved checkpoints to evaluate after training.

Here we provide the checkpoints so you can directly download and evaluate with them.

First download `checkpoint.tar.gz` from <https://drive.google.com/file/d/1RA-wF1hQxLkjVN7R3N1xHkhPDjsEqVv8/view?usp=sharing>. Put it into project root directory.

Now extract the checkpoints:

```bash
# In the project root directory
mkdir checkpoint
tar -xzvf checkpoint.tar.gz -C checkpoint
```

Then replace `rechub.train` in the training commands with `rechub.test` to evaluate the checkpoints.

Note the results you get with the checkpoints could have some difference with the results in paper, since the latter are averaged results.

## Credits

JD Technology (京东科技)

## Cite

```tex
TODO
```
