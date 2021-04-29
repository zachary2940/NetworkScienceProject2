# Torch-RGCN 

Torch-RGCN is a PyTorch implementation of the RGCN, originally proposed by Schlichtkrull *et al.* in  
[Modeling Relational Data with Graph Convolutional Networks](https://arxiv.org/abs/1703.06103).
 
This code was modified from https://github.com/thiviyanT/torch-rgcn, https://github.com/stellargraph/stellargraph and https://github.com/rusty1s/pytorch_geometric

## Getting started

Requirements: 
* Conda >= 4.8
* Python >= 3.7

Do the following: 

1. Download all datasets: `bash get_data.sh` or download using the dropbox links in get_data.sh

2. Install the dependencies inside a new virtual environment: `conda env create -f environment.yml`

3. Activate the virtual environment: `conda activate networkscience`

4. Install the torch-RGCN module: `pip install -e .`  

## Usage

### Configuration files

The hyper-parameters for the different experiments can be found in [YAML](https://yaml.org/) files under 
[configs](configs). The naming convention of the files is as follows: `configs/{MODEL}/{EXPERIMENT}-{DATASET}.yaml`


### Models
* `rgcn` - Standard RGCN Model 
* `c-rgcn` - Compression RGCN Model 
* `e-rgcn` - Embedding RGCN Model

### Experiments
* `rp` - Relation Prediction
* `nc` - Entity Classification 

### Datasets

#### Relation Prediction 

 * `AIFB`  
 * `MUTAG` 
 * `BGS` 
 * `AM` 

#### Entity Classification
 
 * `WN18`  
 * `FB-Toy`
 * `FB15K` 
 * `FB15K-237`

## Part 1: Experiment Reproduction  

### Relation Prediction 

Original Relation Prediction Implementation: https://github.com/MichSchli/RelationPrediction 

To run the relation prediction experiment using the RGCN model using:

`python experiments/predict_relations.py with configs/rgcn/rp-{DATASET}.yaml`

Make sure to replace `{DATASET}` with one of the following dataset names: `FB15k`, `FB15k-237` or `WN18`.

### Entity Classification

Original Entity Classification Implementation: https://github.com/tkipf/relational-gcn

To run the entity classification experiment using the RGCN model using:

`python experiments/classify_entities.py with configs/rgcn/nc-{DATASET}.yaml`

"Batch Training" GPU implementation

`python .\experiments\torch_link_prediction.py --dataset {DATASET}`

Make sure to replace `{DATASET}` with one of the following dataset names: `AIFB`, `MUTAG`, `BGS` or `AM`.

## Part 2: Experiments on New Data

### Relation Prediction 
`python experiments/predict_relations.py with configs/rgcn/rp-FB-toy.yaml`

### Entity Classification
`jupyter notebook`

Navigate to rgcn-node-classification-cora.ipynb to run RGCN classification on Cora dataset

Navigate to rgcn-node-classification.ipynb to run RGCN classification on AIFB dataset


## Dataset References

### Relation Prediction 

 * `AIFB` from 
 Stephan Bloehdorn and York Sure. 
 *[Kernel methods for mining instance data in ontologies.](https://link.springer.com/content/pdf/10.1007%2F978-3-540-76298-0_5.pdf).* 
 In The Semantic Web, 6th International Semantic Web Conference,  2007. 
 * `MUTAG` from 
 A. K. Debnath, R. L. Lopez de Compadre, G. Debnath, A. J.Shusterman, and C. Hansch. 
 *[Structure-activity relationship of mutagenic aromatic and heteroaromatic nitro-compounds correlation 
 with molecular orbital energies and hydrophobicity](https://pubs.acs.org/doi/pdf/10.1021/jm00106a046?casa_token=ECo0FUp3gNoAAAAA:6Xgkt3vGuQeVFnGwlPlyDWm-fIflRmsRe7s5X_SH143O4-wVz5eIMHj_cmDvBWCVon6LLvVt0nTgy-4).* 
 J Med Chem,34:786–797, 1991.
 * `BGS` from 
 de Vries, G.K.D.
 *[A fast approximation of the Weisfeiler-Lehman graph kernel for RDF data](https://link.springer.com/content/pdf/10.1007%2F978-3-642-40988-2_39.pdf).* 
 In European Conference on Machine Learning and Principles and Practice of Knowledge Discovery in Databases, 2013.
 * `AM` from 
de Boer, V., Wielemaker, J., van Gent, J., Hildebrand, M., Isaac, A., van Ossen-bruggen, J., Schreiber, G.
*[Supporting linked data production for cultural heritageinstitutes: The amsterdam museum case study](https://link.springer.com/content/pdf/10.1007%2F978-3-642-30284-8_56.pdf).* 
In The Semantic Web: Research and Applications, 2012.

* `CORA` from 
Qing Lu, and Lise Getoor 
*[Link-based classification](https://linqspub.soe.ucsc.edu/basilic/web/Publications/2003/lu:icml03/)* ICML, 2003. Download Link: https://linqs-data.soe.ucsc.edu/public/lbc/cora.tgz

### Entity Classification
 
 * `WN18` from 
 Antoine Bordes, Nicolas Usunier, Alberto Garcia-Duran , Jason Weston, and Oksana Yakhnenko. 
 *[Translating embeddings for modeling multi-relational data](http://papers.nips.cc/paper/5071-translating-embeddings-for-modeling-multi-rela)*.
 In Advances in Neural Information Processing Systems, 2013. 
 * `FB-Toy` from 
 Daniel Ruffinelli, Samuel Broscheit, and Rainer Gemulla. 
 *[You CAN teach an old dog new tricks! on training knowledge graph embeddings](https://openreview.net/pdf?id=BkxSmlBFvr)*.
 In International Conference on Learning Representations, 2019. 
 * `FB15K` from 
 Antoine Bordes, Nicolas Usunier, Alberto Garcia-Duran , Jason Weston, and Oksana Yakhnenko. 
 *[Translating embeddings for modeling multi-relational data](http://papers.nips.cc/paper/5071-translating-embeddings-for-modeling-multi-rela).*
 In Advances in Neural Information Processing Systems, 2013.
 * `FB15K-237` from 
 Kristina Toutanova and Danqi Chen.
 *[Observed versus latent features for knowledge base and text inference](https://www.aclweb.org/anthology/W15-4007.pdf).*
 In Proceedings of the 3rd Workshop on Continuous Vector Space Models and their Compositionality (CVSC@ACL), 2015.
