# MIMICIII TCN

The notebook in this repository contains a PyTorch implementation of the temporal convolutional network (TCN) for critial care outcome prediction in the MIMIC-III dataset. This work was published in Nature - Scientific Reports on December 8th, 2022.

**Paper:** [Temporal convolutional networks and data rebalancing for clinical length of stay and mortality prediction] (https://www.nature.com/articles/s41598-022-25472-z)

**Cite as:** Bednarski BP, Singh AD, Zhang W, Jones WM, Naeim A, Ramezani R. Temporal convolutional networks and data rebalancing for clinical length of stay and mortality prediction. Sci Rep. 2022;12(1):21247. (doi:10.1038/s41598-022-25472-z)


**Authors:** Bryan P. Bednarski, Akash Deep Singh, Wenhao Zhang, William M. Jones, Arash Naeim, Ramin Ramezani

## Abstract

It is critical for hospitals to accurately predict patient length of stay (LOS) and mortality in real-time. We evaluate temporal convolutional networks (TCNs) and data rebalancing methods to predict LOS and mortality. This is a retrospective cohort study utilizing the MIMIC-III database. The MIMIC-Extract pipeline processes 24 hour time-series clinical objective data for 23,944 unique patient records. TCN performance is compared to both baseline and state-of-the-art machine learning models including logistic regression, random forest, gated recurrent unit with decay (GRU-D). Models are evaluated for binary classification tasks (LOS > 3 days, LOS > 7 days, mortality in-hospital, and mortality in-ICU) with and without data rebalancing and analyzed for clinical runtime feasibility. Data is split temporally, and evaluations utilize tenfold cross-validation (stratified splits) followed by simulated prospective hold-out validation. In mortality tasks, TCN outperforms baselines in 6 of 8 metrics (area under receiver operating characteristic, area under precision-recall curve (AUPRC), and F-1 measure for in-hospital mortality; AUPRC, accuracy, and F-1 for in-ICU mortality). In LOS tasks, TCN performs competitively to the GRU-D (best in 6 of 8) and the random forest model (best in 2 of 8). Rebalancing improves predictive power across multiple methods and outcome ratios. The TCN offers strong performance in mortality classification and offers improved computational efficiency on GPU-enabled systems over popular RNN architectures. Dataset rebalancing can improve model predictive power in imbalanced learning. We conclude that temporal convolutional networks should be included in model searches for critical care outcome prediction systems.

## Instructions for running

1. Clone repository, navigate to directory, build conda environment, install conda kernel to ipykernel:

```
git clone https://github.com/bbednarski9/MIMICIII_TCN/
cd <root/projects_directory>/MIMICIII_TCN/
conda env create -f mimiciii_tcn_conda_env.yml --name mimiciii_tcn_dev
python -m ipykernel install --user --name mimiciii_tcn_dev
```

2. create results and data directories within project

```
mkdir data
mkdir results
```

3. Access MIMIC-III data from PhysioNet (warning: requires credentialed access)

**Registration Link:** https://physionet.org/register/

**MIMIC-III Database:** https://physionet.org/content/mimiciii/1.4/

- download .zip file and save 'all_hourly_data.h5' into newly-created /data directory 

4. Launch jupyter notebooks/labs, select mimic_tcn_dev conda env, and run

## Credit to MIMIC-Extract & PhysioNet

As detailed in the paper, this code is an extension of the MIMIC-Extract published by Shirley Wang and Matthew B. A. McDermott:

**Code**: https://github.com/MLforHealth/MIMIC_Extract

**Paper**: https://dl.acm.org/doi/10.1145/3368555.3384469

Credit for the database goes to the following:
```
Charles, D., King, J., Patel, V. & Furukawa, M. Adoption of Electronic Health record Systems among U.S. Non-federal Acute Care Hospitals. ONC Data Brief No. 9, 1–9 (2013).
Collins, F. S. & Tabak, L. A. NIH plans to enhance reproducibility. Nature 505, 612–613 (2014).
```

## Credit to TCN Authors

The original implementation of the TCN by Bai et. al. (2018) and Locus Lab

**Code**: https://github.com/locuslab/TCN

**Paper**: http://arxiv.org/abs/1803.01271
