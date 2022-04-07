# CS598DLH
reproducibility project for CS598 Deep Learning in Healthcare

## citation to the original paper
Hsieh, K., Wang, Y., Chen, L., Zhao, Z., Savitz, S., Jiang, X., Tang, J. and Kim, Y., 2020. Drug repurposing for COVID-19 using graph neural network with genetic, mechanistic, and epidemiological validation. *Research Square*.

## link to the original paper's repo
https://github.com/yejinjkim/drug-repurposing-graph

## instructions to run the codes
The codes have been tested in Python 3.7.

### 1. install required packages (i.e., dependencies)
```bash
pip install -r requirements.txt
```

### 2. data download instructions
- obtain drug-gene interactions, pathways, and phenotype data of COVID-19 from [CTDbase](https://ctdbase.org/) and locate the files under `./data/CTD/` as shown in the examples below
```
data/CTD/drug-gene-CTD_C0000657245_ixns.tsv
data/CTD/pathways-CTD_D000086382_pathways.tsv
data/CTD/phenotype-drug-gene-CTD_D000086382_diseases.tsv
```
- obtain virus-host protein-protein interaction from Gordon et al. [Nature 2020](https://www.nature.com/articles/s41586-020-2286-9#Sec36) and locate the file as
```
data/biology-database/baits-prey-mist.csv
```
- download pre-trained [DRKG embedding](https://github.com/gnn4dr/DRKG) and locate the files under `./data/DRKG/`
```
data/DRKG/embed/DRKG_TransE_l2_entity.npy
data/DRKG/embed/entities.tsv
data/DRKG/embed/relations.tsv
```
- download curated chemical database from [DrugBank](https://go.drugbank.com/releases/latest) and locate the file as
```
data/CTD/drugbank_drugs.csv
```
- download curated chemical database from [ChEMBL](https://chembl.gitbook.io/chembl-interface-documentation/downloads) and locate the file as
```
data/CTD/chembl_compound.csv
```
### 3. run notebooks in the following order
- `preprocessing.ipynb`

    This notebook file will perform preprocessing of the raw data and save the post-processed data as pickle files.
- `embedding_training.ipynb`

    This notebook file will perform the training of VGAE models for different embeddings used in this reproducibility study.
- `prediction_model_comparison.ipynb`

    This notebook file will train different prediction models and save their performance in a single csv file.

## table of results
<table>
<thead>
  <tr>
    <th rowspan="2">Embedding Method</th>
    <th rowspan="2">Accuracy</th>
    <th colspan="5">Ranking models</th>
  </tr>
  <tr>
    <th>Logistic Regression</th>
    <th>Support Vector Machines</th>
    <th>XGBoost</th>
    <th>Random Forest</th>
    <th>Neural network ranking</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="2">COVID-19 alone</td>
    <td>AUROC</td>
    <td>0.6932</td>
    <td>0.6586</td>
    <td>0.6519</td>
    <td>0.5822</td>
    <td>0.6553</td>
  </tr>
  <tr>
    <td>AUPRC</td>
    <td>0.1017</td>
    <td>0.1319</td>
    <td>0.0842</td>
    <td>0.0666</td>
    <td>0.0861</td>
  </tr>
  <tr>
    <td rowspan="2">DRKG alone</td>
    <td>AUROC</td>
    <td>0.8436</td>
    <td>0.8842</td>
    <td>0.8579</td>
    <td>0.8432</td>
    <td>0.8658</td>
  </tr>
  <tr>
    <td>AUPRC</td>
    <td>0.1839</td>
    <td>0.2579</td>
    <td>0.1426</td>
    <td>0.1331</td>
    <td>0.1744</td>
  </tr>
  <tr>
    <td rowspan="2">hybrid</td>
    <td>AUROC</td>
    <td>0.9004</td>
    <td>0.6670</td>
    <td>0.8746</td>
    <td>0.8698</td>
    <td>0.8915</td>
  </tr>
  <tr>
    <td>AUPRC</td>
    <td>0.2656</td>
    <td>0.2637</td>
    <td>0.2050</td>
    <td>0.2120</td>
    <td>0.2400</td>
  </tr>
</tbody>
</table>
