# TF-SUM: Training-free Video Summarization via Language-based Hierarchical Scoring
> **TF-SUM**  is an innovative video summarization framework that generates high-quality video summaries without any training or manual annotations. It fully leverages the capabilities of pre-trained Large Vision-Language Models (LVLMs) and Large Language Models (LLMs). Specifically, an LVLM is first used to generate textual descriptions for each video frame, with noisy captions filtered via cross-modal similarity. Then, an LLM performs hierarchical importance scoring based on the textual summaries to produce both frame-level and segment-level scores. Finally, visual similarity is used to remove redundant content and refine the importance distribution. **TF-SUM** demonstrates strong performance on two public benchmarks, TVSum and SumMe.*

## Hardware 
- **GPUs**: 2 × NVIDIA Tesla V100-SXM2-32GB  
- **CPU**: Standard compute node (details not specified)  
- **CUDA Version**: 12.2  
- **Operating System**: Ubuntu 20.04.5 LTS  
> Note: TF-SUM is training-free, but efficient inference with LVLMs and LLMs requires GPUs with sufficient memory (24GB+ recommended).

## Getting Started

1. Clone the repository to your local machine:
   ```bash
   git clone 
   cd TFSUM
   ```
2. Set up the conda environment:
   ```bash
   conda create --name TFSUM python=3.10
   conda activate TFSUM
   pip install -r requirements.txt
   ```

##  Datasets

1. Download the **TVSum** and **SumMe** datasets:

    **TVSum**: [https://github.com/yalesong/tvsum](https://github.com/yalesong/tvsum)  
    **SumMe**: [https://opendatalab.org.cn/OpenDataLab/SumMe](https://opendatalab.org.cn/OpenDataLab/SumMe)

2. Organize the datasets as follows:

    Place the **source videos** into the `/videos` subdirectory under each dataset folder.

    For **TVSum**:
      Copy `ydata-tvsum50.mat` into `datasets/TVSum/annotations/`

    For **SumMe**:
      Extract the `GT` folder and place its contents into `datasets/SumMe/annotations/`

3. Download the **preprocessed HDF5 annotation files**:

    [eccv16_dataset_tvsum_google_pool5.h5](https://www.sendgb.com/upload/?utm_source=igjvxR46m5I) → place into `datasets/TVSum/annotations/`
   
    [eccv16_dataset_summe_google_pool5.h5](https://www.sendgb.com/upload/?utm_source=igjvxR46m5I) → place into `datasets/SumMe/annotations/`
```
datasets/
├── TVSum/
│   ├── videos/
│   │   └── ... (original TVSum video files)
│   └── annotations/
│       ├── ydata-tvsum50.mat
│       └── eccv16_dataset_tvsum_google_pool5.h5
│
└── SumMe/
    ├── videos/
    │   └── ... (original SumMe video files)
    └── annotations/
        ├── GT/  (extracted ground truth files)
        └── eccv16_dataset_summe_google_pool5.h5
```
> Make sure the folder structure and filenames are correct, as the system relies on these paths for loading data.
