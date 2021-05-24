# LSEC-GNN

The repository contains the details about our paper **[Leveraging Tripartite Interaction Information from Live Stream E-Commerce for Improving Product Recommendation](https://arxiv.org/abs/TODO.pdf)** (KDD 2021).

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

If there are any problems with later commands, try to install this specific version ([Pypi](https://pypi.org/project/rechub/TODO/), [GitHub](https://github.com/yusanshi/RecHub/tree/TODO-hash)):

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

Each line of commands corresponds to a method in the above table.

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

### Test

You can run the training commands with parameter `--save_checkpoint True` and save the checkpoints and use them to evaluate.

Here we provide the checkpoints so you can directly download and evaluate with them.

```
```

Then replace `rechub.train` in the training commands with `rechub.test` to evaluate the checkpoints.

## Credits

JD Technology (京东科技)

## Cite

```TODO

```
