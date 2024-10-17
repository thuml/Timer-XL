# Timer-XL

Timer-XL: Long-Context Transformers for Unified Time Series Forecasting [[arxiv]](https://arxiv.org/abs/2410.04803).


## Introduction

Timer-XL is a generative Transformer for unified time series forecasting, a mininally tailored scalable backbone for making long-context, aribitray-length and any-variable predictions.

<p align="center">
<img src="./figures/motivation.png" alt="" align=center />
</p>

💪 Based on forecasting principles, we advocate to **extend the context length** in the time series field. 

💡 To facilitate long-context Transformers on diverse tasks, we propose **multivariate next token prediction**, a novel paradigm to uniformly predict 1D and 2D time series with optional covariates. 

🌟 We present Timer-XL enhanced by a universal **TimeAttention** as an extra-long version of generative time-series Transformers ([Timer](https://github.com/thuml/Large-Time-Series-Model)) for unified time series forecasting.

🏆 Timer-XL achieves **state-of-the-art** on both supervised performance and generalization capabilities as a one-for-all large time series model.



## What is New

> For our previous large time series model, please refer to [**Tim**e-Series-Transform**er** (Timer)](https://github.com/thuml/Large-Time-Series-Model)

### Model Architecture

| Time-Series Transformers                      | PatchTST | iTransformer | Moiria | Timer | Timer-XL |
| --------------------------------------------- | -------- | ------------ | ------ | ----- | -------- |
| Generative Model (Causality, Flexible Length) | No       | No           | No     | Yes   | **Yes**  |
| Fine-Grained Modeling of Temporal Dynamics        | Yes      | No           | Yes    | Yes   | **Yes**  |
| Explicit Modeling of Variate Correlation          | No       | Yes          | Yes    | No    | **Yes**  |

### Real-World Benchmark

We establish new forecasting benchmarks with yearly contexts and correlated variables based on [ECMWF Reanalysis v5 (ERA5)](https://www.ecmwf.int/en/forecasts/dataset/ecmwf-reanalysis-v5) for the advancement of this field:

* **ERA5-S (Univariate)**: Three-hour frequency atmospheric dataset spanning 40 years from ERA5, encompassing 116880 time points.

* **ERA5-MS (Multivariate)**: A collection of multi-station ERA5-S datasets to provides partial observations governed by the spatio–temporal weather system.

* **ERA5-Large (Pretrain)**: A larger collection that evenly covers meteorological 4920 worldwide stations, aiming to build a domain-specific large model.

The well-processed datasets and dataloaders will be released soon.

## Generalize 1D Sequences to 2D Time Series

### Multivariate Next Token Prediction

We generalize next token prediction, predominantly adopted for causal generation of 1D sequences to multivariate time series. **Each prediction is made based on tokens of the previous time from multiple variables**:

<p align="center">
<img src="./figures/mntp.png" alt="" align=center />
</p>


### Universal TimeAttention

We introduce TimeAttention, a causal self-attention implmentation for our proposed paradigm, which enables intra- and inter-series modeling with position perception, and maintains the causality and flexibility of generative Transformers. The formulation is also generalizable to univariate and covariate-informed contexts with pre-defined variable dependency, enabling **unified time series forecasting**.

<p align="center">
<img src="./figures/timeattention.png" alt="" align=center />
</p>

## Main Results

<p align="center">
<img src="./figures/performance.png" alt="" align=center />
</p>

## Citation

If you find this repo helpful, please cite our paper. 

```
@article{liu2024timer,
  title={Timer-XL: Long-Context Transformers for Unified Time Series Forecasting},
  author={Liu, Yong and Qin, Guo and Huang, Xiangdong and Wang, Jianmin and Long, Mingsheng},
  journal={arXiv preprint arXiv:2410.04803},
  year={2024}
}
```

## Acknowledgement

We appreciate the following GitHub repos a lot for their valuable code and efforts:
- Time-Series-Library (https://github.com/thuml/Time-Series-Library)
- Large-Time-Series-Model (https://github.com/thuml/Large-Time-Series-Model)
- AutoTimes (https://github.com/thuml/AutoTimes)

## Contact

If you have any questions or want to use the code, feel free to contact:
* Yong Liu (liuyong21@mails.tsinghua.edu.cn)
* Guo Qin (qinguo24@mails.tsinghua.edu.cn)