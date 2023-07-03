# DIVOTrack: A Novel Dataset and Baseline Method for Cross-View Multi-Object Tracking in DIVerse Open Scenes

This repository contains the details of dataset and the Pytorch implementation of Baseline Method CrossMOT of the Paper:
[DIVOTrack: A Novel Dataset and Baseline Method for Cross-View Multi-Object Tracking in DIVerse Open Scenes](https://arxiv.org/abs/2302.07676)


## Abstract
Cross-view multi-object tracking aims to link objects between frames and camera views with substantial overlaps. Although cross-view multi-object tracking has received increased attention in recent years, existing datasets still have several issues, including 1) missing real-world scenarios, 2) lacking diverse scenes, 3) owning a limited number of tracks, 4) comprising only static cameras, and 5) lacking standard benchmarks, which hinder the investigation and comparison of cross-view tracking methods. To solve the aforementioned issues, we introduce **DIVOTrack**: a new cross-view multi-object tracking dataset for **DIV**erse **O**pen scenes with dense tracking pedestrians in realistic and non-experimental environments. Our DIVOTrack has ten distinct scenarios and 550 cross-view tracks, surpassing all cross-view multi-object tracking datasets currently available. Furthermore, we provide a novel baseline cross-view tracking method with a unified joint detection and cross-view tracking framework named CrossMOT, which learns object detection, single-view association, and cross-view matching with an all-in-one embedding model. Finally, we present a summary of current methodologies and a set of standard benchmarks with our DIVOTrack to provide a fair comparison and conduct a comprehensive analysis of current approaches and our proposed CrossMOT.


- Dataset Description
  - Dataset Structure
  - Dataset Downloads
- Training Detector
- Single-view Tracking
- Cross-view Tracking
- TrackEval
- Multi_view_Tracking
- MOTChallengeEvalKit_cv_test


The test result of the cross-view MOT baseline method *MvMHAT* on the DIVOTrack. 
![test.gif](asset/test.gif)

The ground truth of the DIVOTrack.
![gt.gif](asset/gt.gif)

## Dataset Description
We collect data in 10 different real-world scenarios, named: `'Circle', 'Shop', 'Moving', 'Park', 'Ground', 'Gate1', 'Floor', 'Side', 'Square', 'Gate2'`. All
the sequences are captured by using 3 moving cameras: `'View1', 'View2', 'View3'` and are manually synchronized. 

In the old version, the corresponding scenarios named: `'circleRegion', 'innerShop', 'movingView', 'park', 'playground', 'shopFrontGate', 'shopSecondFloor', 'shopSideGate', 'shopSideSquare', 'southGate'`. The corresponding camera named: `'Drone', 'View1', 'View2'`.

### Dataset Structure
The structure of our dataset as:
```
DIVOTrack
    └─────datasets
             └─────DIVO
                    ├───images
                    │    ├───annotations
                    │    ├───dets
                    │    ├───train
                    │    └───test
                    ├───labels_with_ids
                    │    ├───train
                    │    └───test
                    ├───ReID_format
                    │    ├───bounding_box_test
                    │    ├───bounding_box_train
                    │    └───query
                    └───boxes.json

```
### Dataset Downloads
The whole dataset can download from [GoogleDrive](https://drive.google.com/drive/folders/1RCk95TdFv3Tt7gVuyxJasiHG1IPE6jkX?usp=sharing). **Note that, each file needs to unzip by the password. You can decompress each `.zip` file in its folder after send us (shengyuhao@zju.edu.cn, gaoangwang@intl.zju.edu.cn) the License in any format.** After that, you should run `generate_ini.py` to generate `seqinfo.ini` file. 

## Training Detector
The training process of our detector is in `./Training_detector/` and the details can see from  [Training_detector/README.md](https://github.com/shengyuhao/DIVOTrack/tree/main/Training_Detector#readme).
## Single-view Tracking
We conducted experiments on DIVOTrack in fix benchmarks:


| Benchmark | HOTA ↑ | IDF1 ↑ | MOTA ↑ | MOTP ↑ | MT ↑ | ML ↓ | AssA ↑ | IDSw ↓ | FM ↓ |
| --------- | ------ | ------ | ------ | ------ | ---- | ---- | ------ | ------ | ---- |
| [DeepSort](./Single_view_Tracking/Deepsort/) | 52.3 | 58.3 | 76.3 | 81.0 | 382 | 73 | 43.6 | 2,013 | 2,521 |
| [CenterTrack](./Single_view_Tracking/CenterTrack/) | 54.2 | 61.0 | 72.3 | 80.3 | 479 | 49 | 48.1 | 1,732 | 2,438 |
| [Tracktor](./Single_view_Tracking/Tracktor/) | 46.7 | 54.5 | 63.7 | 80.4 | 420 | 33 | 39.3 | 1,517 | 3,601 |
| [FairMOT](./Single_view_Tracking/FairMOT/) | 62.7 | 76.1 | 78.8 | 81.8 | 417 | 66 | 60.9 | 788 | 3,725 |
| [TraDeS](./Single_view_Tracking/TraDeS/) | 57.5 | 66.0 | 72.6 | 82.0 | 467 | 53 | 52.9 | 1,341 | 2,612 |

We evaluate each single-view tracking baseline using `./TrackEval`, and the details can see from [TrackEval/README.md](https://github.com/shengyuhao/DIVOTrack/tree/main/TrackEval#readme).
## Cross-view Tracking
We conducted experiments on the DIVOTrack dataset using six benchmarks as well as our proposed method [CrossMOT](./CrossMOT/)
| Benchmark | CVMA ↑ | CVIDF1 ↑ |
| --------- | ------ | -------- |
| [OSNet](./Cross_view_Tracking/OSNet/) | 
| [Strong](./Cross_view_Tracking/StrongReID/) |
| [AGW](./Cross_view_Tracking/AGW/) |
| [MvMHAT](./Cross_view_Tracking/MvMHAT/) |
| CT | 
| MGN |
| [CrossMOT](./CrossMOT/) |

## Multi-view Tracking
The multi-view tracking results can be obtained from `./Multi_view_Tracking`, the details can see from [Multi_view_Tracking/README.md](https://github.com/shengyuhao/DIVOTrack/tree/main/Multi_view_Tracking#readme)
## MOTChallengeEvalKit_cv_test
The cross-view evaluation can be obtained from `./MOTChallengeEvalKit_cv_test`, and the details can see from [MOTChallengeEvalKit_cv_test/README.md](https://github.com/shengyuhao/DIVOTrack/tree/main/MOTChallengeEvalKit_cv_test#readme)


## Reference
Any use whatsoever of this dataset and its associated software shall constitute your acceptance of the terms of this agreement. By using the dataset and its associated software, you agree to cite the papers of the authors, in any of your publications by you and your collaborators that make any use of the dataset, in the following format:
```
@article{wangdivotrack,
  title={DIVOTrack: A Novel Dataset and Baseline Method for Cross-View Multi-Object Tracking in DIVerse Open Scenes},
  author={Shenghao Hao, Peiyuan Liu, Yibing Zhan, Kaixun Jin, Zuozhu Liu, Mingli Song, Jenq-Neng Hwang, Gaoang Wang},
  journal={arXiv preprint arXiv:2302.07676},
  year={2023}
}
```
The license agreement for data usage implies the citation of the paper above. Please notice that citing the dataset URL instead of the publications would not be compliant with this license agreement. You can read the LICENSE from [LICENSE](https://github.com/shengyuhao/DIVOTrack/blob/main/LICENSE.md).

## Contact
If you have any concerns, please contact shengyuhao@zju.edu.cn
