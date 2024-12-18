# [ESWA] Are Graphs and GCNs necessary for short-term metro ridership forecasting?

This package provides an implementation of SDT-GRU for traffic flow prediction, as described in our paper: 
Qiong Yang , Xianghua Xu, Zihang Wang, Juan Yu, Xiaodong Hu, 
[Are Graphs and GCNs necessary for short-term metro ridership forecasting?](https://doi.org/10.1016/j.eswa.2024.124431),
[Expert Systems with Applications](https://www.sciencedirect.com/journal/expert-systems-with-applications)
> The code is provided by Zihang Wang

![Transformer encoder layer](https://ars.els-cdn.com/content/image/1-s2.0-S0957417424012971-gr1.jpg)
![DT-GRU](https://ars.els-cdn.com/content/image/1-s2.0-S0957417424012971-gr2.jpg)
![SDT-GRU](https://ars.els-cdn.com/content/image/1-s2.0-S0957417424012971-gr3.jpg)

## Requirements

Our code is based on Python version 3.10.12 and PyTorch version 2.0.1.

## Data

[Google Drive](https://drive.google.com/file/d/1XLHEgKdsqvhvxTdmg7Jq3fmyRu6f_1-u/view?usp=sharing)


## Cite

If you find the paper useful, please cite as following:

```
@article{YANG2024124431,
    title = {Are Graphs and GCNs necessary for short-term metro ridership forecasting?},
    journal = {Expert Systems with Applications},
    volume = {254},
    pages = {124431},
    year = {2024},
    issn = {0957-4174},
    doi = {https://doi.org/10.1016/j.eswa.2024.124431},
    url = {https://www.sciencedirect.com/science/article/pii/S0957417424012971},
    author = {Qiong Yang and Xianghua Xu and Zihang Wang and Juan Yu and Xiaodong Hu},
    keywords = {Metro ridership prediction, Transformer encoder, GRU, Encoder–decoder architecture, Graph convolutional networks (GCNs)},
    abstract = {Short-term metro ridership prediction is of great significance to efficient and economic operation of Urban Rail Transit (URT) systems. With the popularity of Graph Convolution Networks (GCN) and Transformers, the recent notable metro ridership forecasting methods are GCN-based and Transformer-based models. However, existing methods face the following drawbacks. First, GCN-based models fail to effectively capture global spatial correlations which are significant for accurate prediction. Second, Transformer-based models are prone to loss temporal information due to the permutation-invariant and anti-order properties of the self-attention which they used for capturing temporal correlations. To overcome the drawbacks, we propose a novel sequence-to-sequence metro ridership prediction model, named SDT-GRU, with Stacked DT-GRU layers as both encoder and decoder. The core component of our model is DT-GRU, which integrates Dual-branch Transformer decoder into the GRU to effectively capture global spatial correlations and temporal correlations with Transformer decoder and GRU, separately. In particular, the DT-GRU module uses one branch Transformer encoder layer to capture spatial correlations within the same timestamp, and adopts another Transformer encoder layer to implicitly capture spatio-temporal correlations among previous timestamps. Then, outputs of the two Transformer encoder layers are fed into a GRU layer to capturing spatio-temporal patterns. To evaluate the effectiveness of the proposed SDT-GRU, we conduct comprehensive experiments on three real-world metro ridership datasets from Beijing, Shanghai and Hangzhou. Experimental results demonstrate that our SDT-GRU achieves better prediction performance than the state-of-the-art baselines.}
}
```

## Benoit Rolland:

### Shared weights
NOT FULLY WORKING SHARE, TO BE UPDATED
for those not having cuda,  wheights calculated whith run_model_<town_suffix>.py were shared [here](https://drive.google.com/drive/folders/19W6QZe1-GdjLpMfi0xBS7r8IXAKnbzYc?usp=sharing)
The log dir was renamed by adding the town suffix in each town dedicared archive

### Fixed Random seed:
Code updated for reproductible results
Here are the expectedly reproductible result for `run_model_HZ.py` with `train: epoch: 1` within `config/hz.yaml`
 
` model.load_state_dict(torch.load(os.path.join(log_dir, 'best.pt')))
2024-12-18 12:03:58,827 - Load best params
2024-12-18 12:03:59,305 - Evaluation_test_Begin:
2024-12-18 12:03:59,306 - Horizon 01, MAE: 90.68, MAPE: 0.4814, RMSE: 196.17
2024-12-18 12:03:59,306 - Horizon 02, MAE: 95.52, MAPE: 0.5068, RMSE: 203.67
2024-12-18 12:03:59,307 - Horizon 03, MAE: 102.78, MAPE: 0.5545, RMSE: 213.22
2024-12-18 12:03:59,307 - Horizon 04, MAE: 107.31, MAPE: 0.7246, RMSE: 217.66
2024-12-18 12:03:59,308 - Average MAE: 99.07, MAPE: 0.5668, RMSE: 207.68
2024-12-18 12:03:59,308 - Evaluation_test_End:`