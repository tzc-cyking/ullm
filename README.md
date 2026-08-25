# Enhancing Multimodal Sentiment Analysis for Missing Modality through Self-Distillation and Unified Modality Cross-Attention


 Enhancing Multimodal Sentiment Analysis for Missing Modality through Self-Distillation and Unified Modality Cross-Attention

Authors: Chenyu Jin, Chenglong Wang, Jun Wang, Honghui Xu*, Shiqing Zhang*, Senior Member IEEE, Jun Yu, and  Qi Tian, Fellow IEEE



## 🔥 News

- :fire:(Aug 25, 2026) The representations used for training have been open sourced! 
- The project page is uploaded on the Github!



## :star: Overview 

The overall architecture:

<div align="center">
<img src="imgs/overall.png" alt="Overall Architectur" />
</div>

Multimodal emotion recognition (MER) under missing modalities remains challenging because unavailable observations must be reconstructed without distorting the underlying affective semantics. Existing generative approaches often treat synthetic representations as faithful substitutes for real modalities, overlooking the semantic drift and representation mismatch introduced during generation. To address these issues, we propose ULLM-MER, an unified large language model (LLM)-assisted framework for audio--text emotion recognition under complete and missing modality conditions. ULLM-MER performs bidirectional modality simulation using frozen pretrained generative models and introduces a dual-level alignment to reduce the discrepancy between real and simulated representations. It further develops a multi-level modality-aware feature fusion mechanism that combines the designed adaptive angular-calibrated directional cross-attention module with a hierarchical multi-view aggregation. Experiments on CMU-MOSI and CMU-MOSEI demonstrate that ULLM-MER achieves competitive performance under complete observations and the best average performance across the evaluated missing-rate settings.


## 🚀 Representation
<!-- ## 🚀 Weights & Representation -->
<!-- 
| Model | Complete Modality MSE | Modality Missing(missing rate 0.7) ACC2  | Link                                                         |
| :---- | --------------------- | -------------------------  | ------------------------------------------------------------ |
| ULLM | 0.517                | 73.5%                    |  [[Google Drive]](https://drive.google.com/file/d/1qDM47_lG0B2eXKVJ8nrx7iOFrd-bD9hC/view?usp=sharing) |


Representation:
[Baidu Drive](https://pan.baidu.com/s/1iHbWPZps-uidqRflAnKnFw?pwd=cqdb) -->
```
https://pan.baidu.com/s/1iHbWPZps-uidqRflAnKnFw?pwd=cqdb -> 
features_mosei/manet_FRA 
features_mosei/vicuna-7b-v1.5-FRA-wavlm2vicuna-half-gt
features_mosei/vicuna-7b-v1.5-FRA-wavlm2vicuna-half-wav+prompt[take_generate_wordembed_-4]
features_mosei/wavlm-large-FRA_-5
```

Dataset Labels
[[Google Drive]](https://drive.google.com/file/d/1-k9A9kFnIlk94QY6nMbc2r3pTu6btU3p/view?usp=sharing)
```
label_official.npz -> dataset/datasets_label/cmumosei-process/
```

## 🔧 Usage

### Requirements

Python >= 3.9

Pytorch >= 1.8.0

```
pip install -r requirements.txt
```



### Inference & Evaluation

If you wish to run inference to evaluate the model's performance, please download the model weights and modality representations into their respective directories. The directory structure should be as follows:

```
└── dataset
    ├── datasets_label
    │   └── cmumosei-process
	│		└── label_official.npz
    └── features_mosei
        ├── manet_FRA
        ├── vicuna-7b-v1.5-FRA-wavlm2vicuna-half-gt
        ├── vicuna-7b-v1.5-FRA-wavlm2vicuna-half-wav+prompt[take_generate_wordembed_-4]
        └── wavlm-large-FRA_-5
```

Run the script to view inference results: 

```shell
bash ./shell/main_text_missing_icassp_inference.sh
```



### Training

#### Training with extracted representations

If you want to directly use the representations we have extracted for you to train the model, you can download the representations directly from the README link and run the following script directly:

```shell
bash ./shell/main_text_missing_icassp.sh
```

#### Training with representations extracted by yourself

If you want to extract representations yourself for related experiments, you can refer to the following configuration.

**Build ./tools folder**

```
## for face extractor (OpenFace-win)
https://drive.google.com/file/d/1-O8epcTDYCrRUU_mtXgjrS3OWA4HTp0-/view?usp=share_link  -> tools/openface_win_x64
## for visual feature extraction
https://drive.google.com/file/d/1wT2h5sz22SaEL4YTBwTIB3WoL4HUvg5B/view?usp=share_link ->  tools/manet

## for audio extraction
https://www.johnvansickle.com/ffmpeg/old-releases ->  tools/ffmpeg-4.4.1-i686-static
## for acoustic features
https://huggingface.co/microsoft/wavlm-large -> tools/transformers/wavlm-large

## for text features
https://huggingface.co/lmsys/vicuna-7b-v1.5 ->  tools/transformers/vicuna-7b-v1.5

## for simulated text representation
# details: https://github.com/X-LANCE/SLAM-LLM/blob/main/examples/asr_librispeech/README.md
https://drive.google.com/file/d/1cLNuMR05oXxKj8M_Z3yAZ5JHJ06ybIHp/view?usp=sharing  ->  tools/transformers/WalmL2VicunaV1.5_model.pt
```

## for simulated audio representation
# details: [https://github.com/FunAudioLLM/CosyVoice](https://github.com/QwenAudio/CosyVoice)

```

You can refer to the run.sh file in each directory of `./features_extraction` to extract each representation.




## :computer: Results

This work ablates various designs of the model and demonstrates the effectiveness of each design.

<div align="center">
<img src="imgs/table_1.png" alt="Ablation Experiment" width=600/>
</div>


Compared with recent models that have performed well on this task, our model achieves optimal performance in both complete and missing modes.

<div align="center">
<img src="imgs/table_2.png" alt="Performance Comparison" width=600/>
</div>



## 🌠 Acknowledgements

Thanks to open source repository [MERTools](https://github.com/zeroQiaoba/MERTools), we have done a lot of work based on it.

<!-- 


```
