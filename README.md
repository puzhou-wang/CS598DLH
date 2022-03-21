# CS598DLH
reproducibility project for CS598 Deep Learning in Healthcare

The paper reproduced here is *Drug repurposing for COVID-19 using graph neural network with genetic, mechanistic, and epidemiological validation* (DOI: [10.21203/rs.3.rs-114758/v1](https://dx.doi.org/10.21203%2Frs.3.rs-114758%2Fv1)).

## instructions to run the codes
The codes have been tested in Python 3.7.

### 1. install required packages
```bash
pip install -r requirements.txt
```

### 2. download the required data
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
