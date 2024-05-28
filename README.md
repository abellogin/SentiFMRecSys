# SentiFMRecSys

Dataset and pretrained models have been uploaded separately due to size constraints: \*Link here\*

1. __Set up a Conda environment with all the necessary libraries__:
    - Create environment: `conda env create -f environment.yml`
    - Activate environment: `conda activate lastfm_sentiment_umap_24`
    - If CUDA (GPU) isn't available at first, consider rebooting the system

2. __Train and evaluate [models](https://recbole.io/docs/user_guide/model_intro.html) with the preprocessed dataset in *dataset/lastfm_recbole-dataset.pth*__:
    - `python3 recbole_run.py --dataset lastfm_recbole --config_files config/generic.yaml -m [Model]`
    - Add `--save` option to save the model in "saved/" as .pth file

3. __Train and evaluate [models](https://recbole.io/docs/user_guide/model_intro.html) by preprocessing the dataset from scratch (takes about ~8GB RAM)__:
    - `python3 recbole_run.py --dataset lastfm_recbole --config_files config/generic_unprocessed.yaml -m [Model]`

4. __Evaluate saved models__:
    - `python3 recbole_run.py --dataset lastfm_recbole --config_files config/generic.yaml --evaluate_model saved/[Saved Model].pth`
    - Add `--evaluation_mode [full | uniN | popN]` to specify [evaluation method](https://recbole.io/docs/user_guide/train_eval_intro.html#evaluation-method), default is **uni100**
    - Some pretrained models are included, trained with the following embeddings:
      - **v (valence)**
      - **a (arousal)**
      - **d (dominance)**
      - **stsc (sentiment ratio)**
