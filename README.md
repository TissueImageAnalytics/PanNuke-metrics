# PanNuke Evaluation Metrics

This repository calculates metrics on the PanNuke dataset, as reported in: <br />

**"PanNuke Dataset Extension, Insights and Baselines"** <br />

The PanNuke dataset can be downloaded [here](https://warwick.ac.uk/fac/sci/dcs/research/tia/data/pannuke). <br />
In the repository, the metrics that are calculated are: <br />

- **Binary PQ (bPQ)**: Assumes all nuclei belong to same class and reports the average PQ across tissue types. <br />
- **Multi-Class PQ (mPQ)**: Reports the average PQ across the classes and tissue types. <br />
- **Neoplastic PQ**: Reports the PQ for the neoplastic class on all tissues. <br />
- **Non-Neoplastic PQ**: Reports the PQ for the non-neoplastic class on all tissues. <br />
- **Inflammatory PQ**: Reports the PQ for the inflammatory class on all tissues. <br />
- **Connective PQ**: Reports the PQ for the connective class on all tissues. <br />
- **Dead PQ**: Reports the PQ for the dead class on all tissues. <br />


For detection based metrics, we used [this function](https://github.com/vqdang/hover_net/blob/master/src/compute_stats.py#L13).

## Set up envrionment

```
conda create --name pannuke python=3.6
conda activate pannuke
pip install -r requirements.txt
```

## Running the Code 

Usage:
```
"""run.

Usage:
  run.py --true_path=<n> --pred_path=<n> --save_path=<n>
  run.py (-h | --help)
  run.py --version
```

Options:
```
  -h --help          Show this string.
  --version          Show version.
  --true_path=<n>    Root path to where the ground-truth is saved.
  --pred_path=<n>    Root path to where the predictions are saved.
  --save_path=<n>    Path where the prediction CSV files will be saved
```

Before running the code, ground truth and predictions must be saved in the following structure: <br />

- True Masks:
    - `<true_path>/masks.npy`
- True Tissue Types:
    - `<true_path>/types.npy`
- Prediction Masks:
    - `<pred_path>/masks.npy`

Here, prediction masks are saved in the same format as the true masks. i.e a single `Nx256x256xC` array, where `N` is the number of test images in that specific fold and `C` is the number of positive classes. The ordering of the channels from index `0` to `4` is `neoplastic`, `inflammatory`, `connective tissue`, `dead` and `non-neoplastic epithelial`.

## Citation

If using this code, please cite: <br />

```
@inproceedings{gamper2019pannuke,
  title={PanNuke: an open pan-cancer histology dataset for nuclei instance segmentation and classification},
  author={Gamper, Jevgenij and Koohbanani, Navid Alemi and Benet, Ksenija and Khuram, Ali and Rajpoot, Nasir},
  booktitle={European Congress on Digital Pathology},
  pages={11--19},
  year={2019},
  organization={Springer}
}
```
```
@article{gamper2020pannuke,
  title={PanNuke Dataset Extension, Insights and Baselines},
  author={Gamper, Jevgenij and Koohbanani, Navid Alemi and Graham, Simon and Jahanifar, Mostafa and Khurram, Syed Ali and Azam, Ayesha and Hewitt, Katherine and Rajpoot, Nasir},
  journal={arXiv preprint arXiv:2003.10778},
  year={2020}
}
```





