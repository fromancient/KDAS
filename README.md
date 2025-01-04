# KDAS: Knowledge Distillation Framework via Attention Supervision for Polyp Segmentation

This is the implementation of **KDAS: Knowledge Distillation Framework via Attention Supervision for Polyp Segmentation** - ICME 2024.  
**Authors:** Quoc-Huy Trinh, Phuoc-Thao Vo Thi, and Minh-Van Nguyen  
**Paper link:** [Arxiv](https://arxiv.org/abs/2312.08555)

## Installation

To install all the packages required for training, please use the `requirements.txt` file. Follow this command to install:

```bash
pip install -r requirements.txt
```

## Dataset

For the dataset, we follow the settings of **PraNet**. We also provide the data in this [Google Drive link](#) for download. After downloading the dataset, unzip the training and testing data, then place them into the `./data/` folder for training.

## Training

To train the model, run the `train_kd_paper.py` file using the following command:

```bash
python train_kd_paper.py
```

Alternatively, you can execute the prepared bash script `train.sh`:

```bash
bash train.sh
```

After running the training script, the training process will start. We conducted experiments on an RTX 5000, and it worked well, so please adjust the batch size to avoid out-of-memory (OOM) issues. The teacher weights can be found at **Polyp-PVT** or in my Google Drive. We train our student model on the **PVTV2-B0** backbone, using the architecture from the **Polyp-PVT** teacher. Please place the teacher weights in the `./teacher_weights/` folder.

## Testing

To produce the testing segmented mask, use the `test_paper.py` file with the following command:

```bash
python test_paper.py
```

This will run segmentation on the test dataset and save the results in the folder `/result_map/PolypPVT_vis`. To evaluate the results, please refer to the instructions from **UACANet**. Additionally, we have prepared an evaluation script in the `eval.py` file. You can run the evaluation using the configuration in `./configs/eval.yaml`. The following command will execute the evaluation:

```bash
python run/Eval.py --config configs/eval.yaml --verbose
```

After running the testing file, you can define the ground truth path and the segmented mask in the configuration file. This benchmark follows the setup from **PraNet**, which is used in the Polyp Segmentation task. The distilled weights for **Polyp-PVT-B0** (approximately 5M parameters) can be found in Google Drive.

## Results

The following are the mask results from the distilled model during our training and testing:

## Acknowledgments

Thank you for following this setup to help me complete this research.

## References

- **Polyp-PVT**
- **PraNet**
- **UACANet**

## Citation

```bibtex
@INPROCEEDINGS{10687662,
  author={Trinh, Quoc-Huy and Nguyen, Minh-Van and Thi, Phuoc-Thao Vo},
  booktitle={2024 IEEE International Conference on Multimedia and Expo (ICME)},
  title={KDAS: Knowledge Distillation via Attention Supervision Framework for Polyp Segmentation},
  year={2024},
  volume={},
  number={},
  pages={1-6},
  keywords={Image segmentation; Accuracy; Computational modeling; Industry applications; Real-time systems; Computational efficiency; Biomedical imaging; Polyp Segmentation; Knowledge Distillation; Symmetrical Guiding; Attention Supervision; Deep Learning},
  doi={10.1109/ICME57554.2024.10687662}
}
```
