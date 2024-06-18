
## Dependencies

```bash
conda create -n CORE python=3.7
conda activate CORE
conda install pytorch torchvision cudatoolkit=11.3 -c pytorch
pip install -r requirements
```

## Data pre-processing

Some errors that crop real faces in manipulated videos occur whether select the biggest or highest detection probability face by MTCNN, especially when there are two characters in a video. We solved the problem by using the provided video mask in FF++.

Please run `python prep_w_mask.py --src-root Your_source_directory --dst-root Your_destination_directory --fake-type Deepfakes[Face2Face, FaceSwap, NeuralTextures, DeepFakeDetection, real]`

## Quickstart

* Xception: `python main.py --dataset ff --aug-name None`
* Xception+: `python main.py --dataset ff --aug-name RE`
* Ours: `python main.py --dataset ff --aug-name RE --consistency cos --consistency-rate 1.0`

For the cross-dataset results , three commands are as follows:
* None: `python main.py --dataset ff --aug-name None`
* RaAug: `python main.py --dataset ff --aug-name RaAug --consistency cos --consistency-rate 100.0`
* DFDC_selim: `python main.py --dataset ff --aug-name DFDC_selim --consistency cos --consistency-rate 100.0`


