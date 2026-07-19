<!-- Copyright 2026 SenseTime Group Inc. and/or its affiliates. -->

<div align="center">

# SenseNova-Vision: Vision as Unified Multimodal Generation

</div>

<div align="center">
  <a href="./README.md">English</a> | <a href="./README_CN.md">简体中文</a> | <a href="./README_KO.md">한국어</a>
  <br>

  <a href="https://arxiv.org/abs/2607.06560"><img src="https://img.shields.io/badge/arXiv-SenseNova--Vision-b31b1b.svg" alt="arXiv"></a>
  <a href="./docs/EVAL.md"><img src="https://img.shields.io/badge/Evaluation-Guide-green" alt="Evaluation Guide"></a>
  <a href="https://huggingface.co/sensenova/SenseNova-Vision-7B-MoT"><img src="https://img.shields.io/badge/%F0%9F%A4%97%20HuggingFace-Model-yellow" alt="HuggingFace Model"></a>
  <a href="https://huggingface.co/datasets/sensenova/SenseNova-Vision-Corpus-50M"><img src="https://img.shields.io/badge/%F0%9F%A4%97%20HuggingFace-Dataset-yellow" alt="HuggingFace Dataset"></a>
  <a href="https://huggingface.co/spaces/sensenova/SenseNova-Vision"><img src="https://img.shields.io/badge/%F0%9F%A4%97%20SenseNova--Vision-Demo-Green" alt="SenseNova-Vision Demo"></a>
  <a href="https://modelscope.cn/models/SenseNova/SenseNova-Vision-7B-MoT" target="_blank"><img src="https://img.shields.io/badge/🤖%20ModelScope-Model-blue" alt="ModelScope Model"></a>
  <a href="./LICENSE"><img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg" alt="License"></a>

<br>
  <a href="./assets/showcase/fig2_one_case_for_all.webp"><img src="./assets/showcase/fig2_one_case_for_all.webp" alt="SenseNova-Vision handles diverse vision tasks in a unified model" width="900"></a>

<br>
  <img src="./assets/fig3_system_overview.webp" alt="SenseNova-Vision system overview" width="900">
</div>

## 📣 업데이트 소식

- `[2026.07.08]` [SenseNova-Vision-Corpus-50M](https://huggingface.co/datasets/sensenova/SenseNova-Vision-Corpus-50M) 데이터셋을 공개했습니다.
- `[2026.07.08]` [SenseNova-Vision-7B-MoT](https://huggingface.co/sensenova/SenseNova-Vision-7B-MoT) 모델 가중치를 처음 공개했습니다.
- `[2026.07.08]` SenseNova-Vision [추론 코드](https://github.com/OpenSenseNova/SenseNova-Vision)를 처음 공개했습니다.
- `[2026.07.08]` SenseNova-Vision [기술 보고서](https://arxiv.org/abs/2607.06560)를 공개했습니다.

## 🌟 개요

🚀 **SenseNova-Vision**은 컴퓨터 비전을 통합 멀티모달 생성 문제로 정식화합니다. 서로 다른 시각 작업을 통합 멀티모달 모델(UMM)의 기본 텍스트 및 이미지 생성 공간으로 표현합니다. 자연어 지시문과 선택적 시각 프롬프트는 작업, 대상 영역 또는 시점, 출력 스키마, 디코딩 규칙을 지정하고, 모델은 기본 텍스트, 이미지 또는 텍스트-이미지 혼합 생성으로 응답합니다.

텍스트 생성은 카테고리, 박스, 포인트, OCR 문자열, 키포인트, 카메라 파라미터 같은 기호적 시각 기록을 표현합니다. 이미지 생성은 세그멘테이션 마스크, 깊이 맵, 표면 법선, 멀티뷰 포인트 맵 같은 조밀한 공간 타깃을 처리합니다. 혼합 응답은 기호 출력과 조밀한 출력을 결합하는 구성적 작업을 지원합니다. 이러한 공통 정식화 덕분에 하나의 모델이 구조화된 시각 이해, 조밀한 기하 예측, 세그멘테이션, 멀티뷰 시각 기하를 포괄하면서도 표준 벤치마크에서 디코딩 가능한 출력을 유지할 수 있습니다.

대규모 학습을 가능하게 하기 위해, 다양한 컴퓨터 비전 어노테이션을 지시문-응답 예제로 변환하고 디코딩 가능한 텍스트, 이미지, 텍스트-이미지 혼합 타깃을 아우르는 **SenseNova-Vision Corpus**를 구축했습니다. SenseNova-Vision은 범용 사전학습 UMM에서 출발해 주로 이 코퍼스로 학습되며, 일반 이해 및 생성 능력을 유지하기 위해 보조 멀티모달 데이터를 함께 사용합니다. 작업별 예측 헤드, 디코더 또는 별도 아키텍처 분기는 필요하지 않습니다.

### 🏗️ 주요 기여

- 🔗 서로 다른 컴퓨터 비전 작업을 UMM의 기본 입출력 공간으로 변환하는 통합 멀티모달 생성 정식화를 제안합니다.
- 🧩 디코딩 가능한 텍스트, 이미지, 텍스트-이미지 혼합 타깃을 포함하는 대규모 컴퓨터 비전 지시문-응답 코퍼스인 SenseNova-Vision Corpus를 구축합니다.
- ✨ SenseNova-Vision을 학습하고, 구조화된 시각 이해, 조밀한 기하 예측, 세그멘테이션, 멀티뷰 시각 기하 전반에서 강력한 결과를 보이며, 고정된 벤치마크 스키마를 넘어 언어로 정의된 작업 변형도 지원함을 보입니다.

## 🛠️ 빠른 시작

이 저장소는 예제 실행, 단일 이미지 추론, 대화형 추론, 벤치마크 추론을 위한 하나의 진입점을 제공합니다. 전체 실행 가이드는 [`docs/EVAL.md`](./docs/EVAL.md)를 참고하세요.

저장소 루트에서 환경을 생성합니다.

```bash
git clone https://github.com/OpenSenseNova/SenseNova-Vision.git
cd SenseNova-Vision
bash setup.sh sensenova-vision
conda activate sensenova-vision
```

준비된 예제를 실행합니다.

```bash
bash scripts/run_sensenova_vision.sh example
```

추론 요청 하나를 실행합니다.

```bash
bash scripts/run_sensenova_vision.sh inference \
  binary_seg \
  "person" \
  examples/images/2.jpg
```

웹 데모를 실행합니다. 래퍼는 Gradio를 시작하기 전에 로컬 URL을 출력합니다.
**권장:** 전체 웹 데모에는 80GB GPU 1장이 권장됩니다.

```bash
MODEL_PATH=/path/to/SenseNova-Vision-7B-MoT \
  bash scripts/run_sensenova_vision.sh demo
```

[`docs/data_prepare.md`](./docs/data_prepare.md)에 따라 `datas/`와 `jsonl_generate/`를 준비한 뒤 전체 벤치마크를 실행합니다.
**권장:** 전체 벤치마크에는 최소 8 x 80GB GPU 머신 1대가 권장됩니다.

```bash
bash scripts/run_sensenova_vision.sh benchmark all \
  --num_gpus 8 \
  --tasks_per_gpu 2
```

## 🏆 벤치마크 결과

SenseNova-Vision은 구조화된 시각 이해, 조밀한 기하 예측, 세그멘테이션, 멀티뷰 시각 기하 전반에서 평가됩니다. 모든 작업은 자연어 지시문으로 정식화됩니다. 텍스트 출력은 박스, 포인트, 인식된 텍스트, 키포인트, 카메라 파라미터 같은 벤치마크별 구조로 파싱되고, 이미지 출력은 마스크, 깊이 맵, 법선 맵 또는 3D 포인트 맵으로 디코딩됩니다.

### 구조화된 시각 이해

구조화된 시각 이해는 바운딩 박스, 포인트, 인식된 텍스트, 키포인트 좌표처럼 구조화된 텍스트 예측으로 표현할 수 있는 작업을 평가합니다.

<table>
  <thead>
    <tr>
      <th align="center" rowspan="3">Method</th>
      <th align="center" colspan="6">Object Detection</th>
      <th align="center" colspan="2">OCR</th>
      <th align="center">GUI</th>
      <th align="center">Keypoint</th>
    </tr>
    <tr>
      <th align="center">COCO-Com.</th>
      <th align="center">HR/RefCOCOg V/T</th>
      <th align="center">LVIS</th>
      <th align="center">Dense200</th>
      <th align="center" colspan="2">VisDrone</th>
      <th align="center">HierText</th>
      <th align="center">ICDAR15</th>
      <th align="center">ScreenSpot-V2</th>
      <th align="center">COCO-Kpt.</th>
    </tr>
    <tr>
      <th align="center">bbox</th>
      <th align="center">bbox</th>
      <th align="center">bbox</th>
      <th align="center">bbox</th>
      <th align="center">bbox</th>
      <th align="center">point</th>
      <th align="center">bbox</th>
      <th align="center">bbox</th>
      <th align="center">bbox</th>
      <th align="center">point</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Grounding DINO-Swin-T</td>
      <td><strong>56.6</strong></td>
      <td>25.2 / 45.9 / 46.8</td>
      <td>38.8</td>
      <td>33.1</td>
      <td><u>38.5</u></td>
      <td>--</td>
      <td>--</td>
      <td>--</td>
      <td>--</td>
      <td>--</td>
    </tr>
    <tr>
      <td>Bagel</td>
      <td>50.2</td>
      <td>74.6 / 76.4 / <u>77.8</u></td>
      <td>46.8</td>
      <td>42.4</td>
      <td>23.0</td>
      <td>36.9</td>
      <td>7.1</td>
      <td>15.8</td>
      <td>81.1</td>
      <td>--</td>
    </tr>
    <tr>
      <td>Qwen3-VL-8B-Instruct</td>
      <td>46.6</td>
      <td>70.4 / 72.3 / 72.6</td>
      <td>43.2</td>
      <td>13.5</td>
      <td>28.7</td>
      <td>35.7</td>
      <td>22.4</td>
      <td>25.4</td>
      <td><u>90.5</u></td>
      <td>--</td>
    </tr>
    <tr>
      <td>Qwen3.5-9B</td>
      <td>49.3</td>
      <td>71.7 / 72.1 / 72.6</td>
      <td>43.2</td>
      <td>27.5</td>
      <td>26.8</td>
      <td>41.7</td>
      <td>19.6</td>
      <td>11.4</td>
      <td><strong>92.2</strong></td>
      <td>--</td>
    </tr>
    <tr>
      <td>LocateAnything</td>
      <td><u>54.7</u></td>
      <td>78.7 / <u>76.7</u> / 77.6</td>
      <td><u>50.7</u></td>
      <td><u>58.7</u></td>
      <td><u>39.9</u></td>
      <td><u>60.4</u></td>
      <td><u>29.1</u></td>
      <td>26.4</td>
      <td>85.5</td>
      <td>--</td>
    </tr>
    <tr>
      <td>Rex-Omni</td>
      <td>52.9</td>
      <td><u>79.9</u> / 73.6 / 74.3</td>
      <td>46.9</td>
      <td>58.3</td>
      <td>35.8</td>
      <td>58.9</td>
      <td>28.0</td>
      <td><u>28.1</u></td>
      <td>88.4</td>
      <td><u>32.6</u></td>
    </tr>
    <tr>
      <td>SenseNova-Vision</td>
      <td><strong>56.6</strong></td>
      <td><strong>80.2</strong> / <strong>79.6</strong> / <strong>80.5</strong></td>
      <td><strong>54.8</strong></td>
      <td><strong>66.8</strong></td>
      <td><strong>43.3</strong></td>
      <td><strong>62.9</strong></td>
      <td><strong>31.2</strong></td>
      <td><strong>49.5</strong></td>
      <td>85.9</td>
      <td><strong>34.6</strong></td>
    </tr>
  </tbody>
</table>

### 조밀한 기하 예측

조밀한 기하 예측은 단안 깊이 추정과 표면 법선 추정을 포함해 픽셀 정렬된 기하 출력을 평가합니다.

<table>
  <thead>
    <tr>
      <th align="center" rowspan="3">Method</th>
      <th align="center" colspan="5">Depth</th>
      <th align="center" colspan="3">Normal</th>
    </tr>
    <tr>
      <th align="center">NYUv2</th>
      <th align="center">KITTI</th>
      <th align="center">ETH3D</th>
      <th align="center">ScanNet</th>
      <th align="center">DIODE</th>
      <th align="center">ScanNet</th>
      <th align="center">iBims-1</th>
      <th align="center">NYUv2</th>
    </tr>
    <tr>
      <th align="center" colspan="5">AbsRel↓ / δ1↑</th>
      <th align="center" colspan="3">Mean↓ / 11.25°↑</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>DSINE</td>
      <td>--</td><td>--</td><td>--</td><td>--</td><td>--</td>
      <td>16.2 / 61.0</td><td>17.1 / 67.4</td><td>16.4 / 59.6</td>
    </tr>
    <tr>
      <td>DepthAnything</td>
      <td>4.3 / <strong>98.1</strong></td><td>7.6 / 94.7</td><td>12.7 / 88.2</td><td>4.3 / 98.1</td><td>26.0 / 75.9</td>
      <td>--</td><td>--</td><td>--</td>
    </tr>
    <tr>
      <td>DepthAnything V2</td>
      <td>4.5 / 97.9</td><td>7.4 / 94.6</td><td>13.1 / 86.5</td><td>4.2 / 97.8</td><td>26.5 / 73.4</td>
      <td>--</td><td>--</td><td>--</td>
    </tr>
    <tr>
      <td>*MoGe-2</td>
      <td><strong>3.5</strong> / 98.0</td><td><strong>5.5</strong> / <strong>97.7</strong></td><td><strong>3.4</strong> / <strong>98.8</strong></td><td><strong>3.4</strong> / <strong>98.3</strong></td><td><strong>23.0</strong> / <strong>82.3</strong></td>
      <td><strong>12.8</strong> / <strong>68.4</strong></td><td><strong>14.7</strong> / <strong>70.4</strong></td><td><strong>14.7</strong> / <strong>62.3</strong></td>
    </tr>
    <tr>
      <td>Marigold</td>
      <td>5.5 / 96.4</td><td>9.9 / 91.6</td><td>6.5 / 95.9</td><td>6.4 / 95.2</td><td>30.8 / <u>77.3</u></td>
      <td>21.3 / 45.6</td><td>18.5 / 64.7</td><td>20.9 / 50.5</td>
    </tr>
    <tr>
      <td>DICEPTION</td>
      <td>6.1 / 96.0</td><td>6.9 / 94.9</td><td>5.0 / 97.5</td><td>7.2 / 94.4</td><td>28.9 / 72.2</td>
      <td>18.8 / 53.6</td><td>--</td><td>18.3 / 52.9</td>
    </tr>
    <tr>
      <td>FE2E</td>
      <td><u>4.1</u> / <u>97.7</u></td><td><u>6.6</u> / <strong>96.0</strong></td><td><strong>3.8</strong> / <strong>98.7</strong></td><td>4.4 / 97.5</td><td>22.8 / <strong>81.2</strong></td>
      <td><u>13.8</u> / <u>67.2</u></td><td><strong>15.1</strong> / <strong>70.6</strong></td><td><u>16.2</u> / <u>59.6</u></td>
    </tr>
    <tr>
      <td>Lotus-2</td>
      <td><u>4.1</u> / 97.6</td><td>6.7 / 94.5</td><td>4.6 / <u>98.1</u></td><td><u>4.2</u> / <u>97.6</u></td><td><u>22.1</u> / 75.2</td>
      <td>14.2 / 66.8</td><td><u>15.4</u> / <u>70.4</u></td><td>16.9 / 59.0</td>
    </tr>
    <tr>
      <td>SenseNova-Vision</td>
      <td><strong>4.0</strong> / <strong>98.1</strong></td><td><strong>5.9</strong> / <u>95.9</u></td><td><u>4.3</u> / 97.4</td><td><strong>3.9</strong> / <strong>98.0</strong></td><td><strong>20.6</strong> / 76.4</td>
      <td><strong>12.8</strong> / <strong>68.9</strong></td><td><u>15.4</u> / 69.1</td><td><strong>14.4</strong> / <strong>62.7</strong></td>
    </tr>
  </tbody>
</table>

### 세그멘테이션

세그멘테이션은 의미론적, 참조 기반, 추론 기반, grounded, 인터랙티브 안내 조건에서 마스크 예측을 평가합니다.

<table>
  <thead>
    <tr>
      <th align="center" rowspan="2">Method</th>
      <th align="center">Gen. Seg.</th>
      <th align="center">Ref. Seg.</th>
      <th align="center">Rea. Seg.</th>
      <th align="center">GCG Seg.</th>
      <th align="center">Inter. Seg.</th>
    </tr>
    <tr>
      <th align="center">Pan. / Sem.</th>
      <th align="center">RefCOCO / + / g</th>
      <th align="center">Val / Test</th>
      <th align="center">Val / Test</th>
      <th align="center">Point / Box</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>LISA-7B</td><td>--</td><td>74.9 / 65.1 / 67.9</td><td>52.9 / 47.3</td><td>62.0 / 61.7</td><td>--</td></tr>
    <tr><td>PSALM</td><td><strong>55.9</strong> / <strong>66.6</strong></td><td>83.6 / 72.9 / 73.8</td><td>--</td><td>--</td><td><u>64.3</u> / 67.3</td></tr>
    <tr><td>Text4Seg</td><td>--</td><td>79.2 / 72.8 / 74.0</td><td>59.1 / 57.1</td><td>--</td><td>--</td></tr>
    <tr><td>LENS</td><td>--</td><td><u>84.2</u> / <strong>79.4</strong> / <u>81.2</u></td><td><u>62.1</u> / 57.2</td><td>--</td><td>--</td></tr>
    <tr><td>ConverSeg</td><td>--</td><td>79.4 / 74.3 / 74.9</td><td>61.9 / 57.0</td><td>--</td><td>--</td></tr>
    <tr><td>X-SAM</td><td><u>54.7</u> / <u>66.5</u></td><td><strong>85.1</strong> / <u>78.0</u> / <strong>83.8</strong></td><td>56.6 / <u>57.8</u></td><td><strong>69.4</strong> / <strong>69.0</strong></td><td><strong>65.4</strong> / <u>70.0</u></td></tr>
    <tr><td>SenseNova-Vision</td><td>48.8 / 64.0</td><td>81.3 / 76.0 / 80.3</td><td><strong>63.2</strong> / <strong>60.7</strong></td><td><u>65.7</u> / <u>66.2</u></td><td>60.9 / <strong>73.9</strong></td></tr>
  </tbody>
</table>

### 멀티뷰 시각 기하

멀티뷰 시각 기하는 멀티뷰 포인트 맵 재구성과 카메라 포즈 추정을 포함해 여러 입력 이미지에서의 기하 예측을 평가합니다.

<table>
  <thead>
    <tr>
      <th align="center" rowspan="3">Method</th>
      <th align="center" colspan="2">Multi-View Reconstruction</th>
      <th align="center" colspan="2">Camera Pose</th>
    </tr>
    <tr>
      <th align="center" colspan="2">Acc.↓ / Comp.↓ / F1↑</th>
      <th align="center" colspan="2">RRA@30↑ / RTA@30↑ / AUC@30↑</th>
    </tr>
    <tr>
      <th align="center">7Scenes</th>
      <th align="center">ETH3D</th>
      <th align="center">Re10K</th>
      <th align="center">CO3Dv2</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>DUSt3R</td><td>0.026 / 0.034 / 87.1</td><td>0.359 / 0.531 / 66.6</td><td>99.8 / 84.9 / 67.6</td><td>97.7 / 93.4 / 78.3</td></tr>
    <tr><td>DepthAnything3</td><td><strong>0.020</strong> / <strong>0.026</strong> / <strong>90.5</strong></td><td>0.228 / 0.212 / 76.6</td><td><strong>100.0</strong> / <strong>96.4</strong> / <strong>89.6</strong></td><td><strong>99.3</strong> / <strong>98.0</strong> / <strong>91.8</strong></td></tr>
    <tr><td>VGGT</td><td>0.023 / 0.032 / 88.4</td><td><strong>0.177</strong> / <strong>0.155</strong> / <strong>80.9</strong></td><td><strong>100.0</strong> / 93.5 / 79.3</td><td>98.3 / 96.6 / 89.2</td></tr>
    <tr><td>MoRe</td><td>0.038 / 0.039 / 77.1</td><td>0.348 / 0.318 / 62.7</td><td><strong>100.0</strong> / 94.0 / 79.1</td><td>98.4 / 96.3 / 83.0</td></tr>
    <tr><td>MapAnything</td><td><strong>0.027</strong> / 0.029 / 87.8</td><td>0.400 / 0.524 / 67.0</td><td><strong>100.0</strong> / 93.5 / <strong>80.7</strong></td><td>95.5 / 91.6 / 70.9</td></tr>
    <tr><td>G2VLM</td><td>0.084 / 0.056 / 59.2</td><td>0.784 / 0.553 / 36.7</td><td>99.8 / 77.5 / 51.8</td><td>96.3 / 92.0 / 55.2</td></tr>
    <tr><td>SenseNova-Vision</td><td>0.028 / <strong>0.026</strong> / <strong>87.9</strong></td><td><strong>0.301</strong> / <strong>0.175</strong> / <strong>72.2</strong></td><td>99.8 / <strong>94.2</strong> / 77.3</td><td><strong>97.4</strong> / <strong>95.4</strong> / <strong>80.1</strong></td></tr>
  </tbody>
</table>

### 범용 비전 모델과의 비교

여러 시각 능력을 포괄하는 최근 범용 비전 모델들과 SenseNova-Vision을 추가로 비교합니다.

<table>
  <thead>
    <tr><th align="center" rowspan="3">Method</th><th align="center">Detection</th><th align="center">Sem. Seg.</th><th align="center">Ref. Seg.</th><th align="center">Depth</th></tr>
    <tr><th align="center">mAP</th><th align="center">mIoU</th><th align="center">cIoU</th><th align="center">δ1</th></tr>
    <tr><th align="center">COCO</th><th align="center">Cityscapes</th><th align="center">RefCOCO / + / g</th><th align="center">NYUv2</th></tr>
  </thead>
  <tbody>
    <tr><td>Youtu-VL</td><td>47.1</td><td>70.4</td><td>80.7 / <strong>76.2</strong> / 76.5</td><td>90.4</td></tr>
    <tr><td>SenseNova-Vision</td><td><strong>53.7</strong></td><td><strong>71.2</strong></td><td><strong>81.3</strong> / 76.0 / <strong>80.3</strong></td><td><strong>98.1</strong></td></tr>
  </tbody>
</table>

<table>
  <thead>
    <tr><th align="center" rowspan="3">Method</th><th align="center">Sem. Seg.</th><th align="center">Ref. Seg.</th><th align="center">Rea. Seg.</th><th align="center" colspan="4">Depth</th><th align="center" colspan="3">Normal</th></tr>
    <tr><th align="center">mIoU</th><th align="center">cIoU</th><th align="center">gIoU</th><th align="center" colspan="4">δ1</th><th align="center" colspan="3">Mean Error↓</th></tr>
    <tr><th align="center">Cityscapes</th><th align="center">RefCOCOg</th><th align="center">ReasonSeg</th><th align="center">KITTI</th><th align="center">NYUv2</th><th align="center">DIODE</th><th align="center">ETH3D</th><th align="center">NYUv2</th><th align="center">ScanNet</th><th align="center">DIODE</th></tr>
  </thead>
  <tbody>
    <tr><td>Vision Banana</td><td>69.9</td><td>73.8</td><td>79.3</td><td>91.5</td><td>94.8</td><td>91.7</td><td>93.5</td><td>17.8</td><td>15.1</td><td><strong>13.8</strong></td></tr>
    <tr><td>SenseNova-Vision</td><td><strong>71.2</strong></td><td><strong>80.3</strong></td><td>63.2</td><td>95.9</td><td>98.1</td><td>76.4</td><td>97.4</td><td><strong>14.4</strong></td><td><strong>12.8</strong></td><td>15.3</td></tr>
  </tbody>
</table>

## 🎨 쇼케이스

<p align="center">
  <a href="./assets/showcase/fig7_sensenova_vision_results.webp"><img src="./assets/showcase/fig7_sensenova_vision_results.webp" alt="SenseNova-Vision qualitative results across vision tasks" width="900"></a>
</p>

<details>
<summary>객체 탐지</summary>

<table align="center">
  <thead>
    <tr>
      <th align="center">COCO-Com.</th>
      <th align="center">LVIS</th>
      <th align="center">Dense200</th>
      <th align="center">VisDrone</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"><a href="./assets/showcase/object_detection/coco_common.jpg"><img height="180" alt="common object detection COCO case" src="./assets/showcase/object_detection/coco_common.jpg"></a></td>
      <td align="center"><a href="./assets/showcase/object_detection/LIVS.jpg"><img height="180" alt="long-tail object detection LVIS case" src="./assets/showcase/object_detection/LIVS.jpg"></a></td>
      <td align="center"><a href="./assets/showcase/object_detection/dense200.jpg"><img height="180" alt="dense object detection Dense200 case" src="./assets/showcase/object_detection/dense200.jpg"></a></td>
      <td align="center"><a href="./assets/showcase/object_detection/visdrone.jpg"><img height="180" alt="object detection VisDrone case" src="./assets/showcase/object_detection/visdrone.jpg"></a></td>
    </tr>
  </tbody>
</table>

</details>

<details>
<summary>참조 탐지</summary>

<table align="center">
  <tr>
    <td align="center"><a href="./assets/showcase/referring_detection/141964854306.jpg"><img height="260" alt="referring detection case 1" src="./assets/showcase/referring_detection/141964854306.jpg"></a></td>
    <td align="center"><a href="./assets/showcase/referring_detection/COCO_train2014_000000204294.jpg"><img height="260" alt="referring detection case 2" src="./assets/showcase/referring_detection/COCO_train2014_000000204294.jpg"></a></td>
  </tr>
</table>

</details>

<details>
<summary>OCR</summary>

<table align="center">
  <tr>
    <th align="center" colspan="2">Textline Level</th>
  </tr>
  <tr>
    <td align="center"><a href="./assets/showcase/ocr/textline_1.jpg"><img height="220" alt="OCR textline case 1" src="./assets/showcase/ocr/textline_1.jpg"></a></td>
    <td align="center"><a href="./assets/showcase/ocr/textline_2.jpg"><img height="220" alt="OCR textline case 2" src="./assets/showcase/ocr/textline_2.jpg"></a></td>
  </tr>
  <tr>
    <th align="center" colspan="2">Word Level</th>
  </tr>
  <tr>
    <td align="center"><a href="./assets/showcase/ocr/word_1.jpg"><img height="220" alt="OCR word case 1" src="./assets/showcase/ocr/word_1.jpg"></a></td>
    <td align="center"><a href="./assets/showcase/ocr/word_2.jpg"><img height="220" alt="OCR word case 2" src="./assets/showcase/ocr/word_2.jpg"></a></td>
  </tr>
</table>

</details>

<details>
<summary>시각 프롬프팅</summary>

<table align="center">
  <tr>
    <td align="center"><a href="./assets/showcase/visual_prompt/2009.jpg"><img height="220" alt="visual prompt bbox case 1" src="./assets/showcase/visual_prompt/2009.jpg"></a></td>
    <td align="center"><a href="./assets/showcase/visual_prompt/2271.jpg"><img height="220" alt="visual prompt bbox case 2" src="./assets/showcase/visual_prompt/2271.jpg"></a></td>
  </tr>
  <tr>
    <td align="center"><a href="./assets/showcase/visual_prompt/2916.jpg"><img height="220" alt="visual prompt bbox case 3" src="./assets/showcase/visual_prompt/2916.jpg"></a></td>
    <td align="center"><a href="./assets/showcase/visual_prompt/7082.jpg"><img height="220" alt="visual prompt bbox case 4" src="./assets/showcase/visual_prompt/7082.jpg"></a></td>
  </tr>
</table>

</details>

<details>
<summary>레이아웃 그라운딩</summary>

<table align="center">
  <tr>
    <td align="center"><a href="./assets/showcase/layout_grounding/layout_1.jpg"><img height="240" alt="layout grounding case 1" src="./assets/showcase/layout_grounding/layout_1.jpg"></a></td>
    <td align="center"><a href="./assets/showcase/layout_grounding/layout_2.jpg"><img height="240" alt="layout grounding case 2" src="./assets/showcase/layout_grounding/layout_2.jpg"></a></td>
  </tr>
</table>

</details>

<details>
<summary>키포인트 탐지</summary>

<table align="center">
  <tr>
    <th align="center" colspan="2">Human</th>
  </tr>
  <tr>
    <td align="center"><a href="./assets/showcase/keypoints/human_1.jpg"><img height="240" alt="human keypoint case 1" src="./assets/showcase/keypoints/human_1.jpg"></a></td>
    <td align="center"><a href="./assets/showcase/keypoints/human_2.jpg"><img height="240" alt="human keypoint case 2" src="./assets/showcase/keypoints/human_2.jpg"></a></td>
  </tr>
  <tr>
    <th align="center" colspan="2">Animal</th>
  </tr>
  <tr>
    <td align="center"><a href="./assets/showcase/keypoints/animal_1.jpg"><img height="240" alt="animal keypoint case 1" src="./assets/showcase/keypoints/animal_1.jpg"></a></td>
    <td align="center"><a href="./assets/showcase/keypoints/animal_2.jpg"><img height="240" alt="animal keypoint case 2" src="./assets/showcase/keypoints/animal_2.jpg"></a></td>
  </tr>
</table>

</details>

<details>
<summary>GUI 그라운딩</summary>

<table align="center">
  <tr>
    <td align="center"><a href="./assets/showcase/gui_grounding/gui_1.jpg"><img height="220" alt="GUI grounding case 1" src="./assets/showcase/gui_grounding/gui_1.jpg"></a></td>
    <td align="center"><a href="./assets/showcase/gui_grounding/gui_2.jpg"><img height="220" alt="GUI grounding case 2" src="./assets/showcase/gui_grounding/gui_2.jpg"></a></td>
  </tr>
</table>

</details>

<details>
<summary>조밀한 기하 예측</summary>

<table align="center">
  <tr>
    <td align="center"><a href="./assets/showcase/dense_geometry/dense_geometry.jpg"><img width="900" alt="dense geometric prediction depth and normal cases" src="./assets/showcase/dense_geometry/dense_geometry.jpg"></a></td>
  </tr>
</table>

</details>
<details>
<summary>파놉틱 세그멘테이션</summary>

<table align="center">
  <tr>
    <td align="center"><a href="./assets/showcase/segmentation/pan/000000439525_panoptic.webp"><img height="240" alt="panoptic segmentation case 1" src="./assets/showcase/segmentation/pan/000000439525_panoptic.webp"></a></td>
    <td align="center"><a href="./assets/showcase/segmentation/pan/000000563603_panoptic.webp"><img height="240" alt="panoptic segmentation case 2" src="./assets/showcase/segmentation/pan/000000563603_panoptic.webp"></a></td>
  </tr>
  <tr>
    <td align="center"><a href="./assets/showcase/segmentation/pan/000000237928_panoptic.webp"><img height="240" alt="panoptic segmentation case 3" src="./assets/showcase/segmentation/pan/000000237928_panoptic.webp"></a></td>
    <td align="center"><a href="./assets/showcase/segmentation/pan/000000009772_panoptic.webp"><img height="240" alt="panoptic segmentation case 4" src="./assets/showcase/segmentation/pan/000000009772_panoptic.webp"></a></td>
  </tr>
</table>

</details>

<details>
<summary>시맨틱 세그멘테이션</summary>

<table align="center">
  <tr>
    <td align="center"><a href="./assets/showcase/segmentation/sem/000000001000_semantic.webp"><img height="240" alt="semantic segmentation case 1" src="./assets/showcase/segmentation/sem/000000001000_semantic.webp"></a></td>
    <td align="center"><a href="./assets/showcase/segmentation/sem/000000017627_semantic.webp"><img height="240" alt="semantic segmentation case 2" src="./assets/showcase/segmentation/sem/000000017627_semantic.webp"></a></td>
  </tr>
  <tr>
    <td align="center"><a href="./assets/showcase/segmentation/sem/000000028993_semantic.webp"><img height="240" alt="semantic segmentation case 3" src="./assets/showcase/segmentation/sem/000000028993_semantic.webp"></a></td>
    <td align="center"><a href="./assets/showcase/segmentation/sem/000000074733_semantic.webp"><img height="240" alt="semantic segmentation case 4" src="./assets/showcase/segmentation/sem/000000074733_semantic.webp"></a></td>
  </tr>
</table>

</details>

<details>
<summary>참조 세그멘테이션</summary>

<table align="center">
  <tr>
    <td align="center"><a href="./assets/showcase/segmentation/ref/sample_003607_COCO_train2014_000000084712_42623_main_center_person_pred_vis.webp"><img height="240" alt="referring segmentation case 1" src="./assets/showcase/segmentation/ref/sample_003607_COCO_train2014_000000084712_42623_main_center_person_pred_vis.webp"></a></td>
    <td align="center"><a href="./assets/showcase/segmentation/ref/sample_003854_COCO_train2014_000000232371_30263_left_giraffe_pred_vis.webp"><img height="240" alt="referring segmentation case 2" src="./assets/showcase/segmentation/ref/sample_003854_COCO_train2014_000000232371_30263_left_giraffe_pred_vis.webp"></a></td>
  </tr>
  <tr>
    <td align="center"><a href="./assets/showcase/segmentation/ref/sample_004283_COCO_train2014_000000388421_16726_older_man_pred_vis.webp"><img height="240" alt="referring segmentation case 3" src="./assets/showcase/segmentation/ref/sample_004283_COCO_train2014_000000388421_16726_older_man_pred_vis.webp"></a></td>
    <td align="center"><a href="./assets/showcase/segmentation/ref/sample_010222_COCO_train2014_000000180179_34673_middle_zebra_pred_vis.webp"><img height="240" alt="referring segmentation case 4" src="./assets/showcase/segmentation/ref/sample_010222_COCO_train2014_000000180179_34673_middle_zebra_pred_vis.webp"></a></td>
  </tr>
</table>

</details>

<details>
<summary>추론 세그멘테이션</summary>

<table align="center">
  <tr>
    <td align="center"><a href="./assets/showcase/segmentation/rea/sample_000128_14013318558_59e559a0a5_o_in_a_music_class_students_usually_learn_to_play_various_instruments.__b2f4083db9_pred_vis.webp"><img height="240" alt="reasoning segmentation case 1" src="./assets/showcase/segmentation/rea/sample_000128_14013318558_59e559a0a5_o_in_a_music_class_students_usually_learn_to_play_various_instruments.__b2f4083db9_pred_vis.webp"></a></td>
    <td align="center"><a href="./assets/showcase/segmentation/rea/sample_001270_4780863298_1e6c37d2b8_o_in_colder_seasons_when_the_weather_can_be_unpredictable_please_identi_8a93ad4d2c_pred_vis.webp"><img height="240" alt="reasoning segmentation case 2" src="./assets/showcase/segmentation/rea/sample_001270_4780863298_1e6c37d2b8_o_in_colder_seasons_when_the_weather_can_be_unpredictable_please_identi_8a93ad4d2c_pred_vis.webp"></a></td>
  </tr>
  <tr>
    <td align="center"><a href="./assets/showcase/segmentation/rea/sample_001431_5183659728_546436cdcb_o_what_object_in_the_picture_could_be_utilized_as_an_accessory_worn_aro_58d636e391_pred_vis.webp"><img height="240" alt="reasoning segmentation case 3" src="./assets/showcase/segmentation/rea/sample_001431_5183659728_546436cdcb_o_what_object_in_the_picture_could_be_utilized_as_an_accessory_worn_aro_58d636e391_pred_vis.webp"></a></td>
    <td align="center"><a href="./assets/showcase/segmentation/rea/sample_001998_7302072422_9c406bf68a_o_when_sailing_on_water_adjusting_the_sails_is_necessary_for_controllin_cd00167b1f_pred_vis.webp"><img height="240" alt="reasoning segmentation case 4" src="./assets/showcase/segmentation/rea/sample_001998_7302072422_9c406bf68a_o_when_sailing_on_water_adjusting_the_sails_is_necessary_for_controllin_cd00167b1f_pred_vis.webp"></a></td>
  </tr>
</table>

</details>

<details>
<summary>Grounded Conversation Generation 세그멘테이션</summary>

<table align="center">
  <tr>
    <td align="center"><a href="./assets/showcase/segmentation/GCG/20260630-192539.webp"><img height="240" alt="grounded conversation generation segmentation case 1" src="./assets/showcase/segmentation/GCG/20260630-192539.webp"></a></td>
    <td align="center"><a href="./assets/showcase/segmentation/GCG/20260630-201751.webp"><img height="240" alt="grounded conversation generation segmentation case 2" src="./assets/showcase/segmentation/GCG/20260630-201751.webp"></a></td>
  </tr>
  <tr>
    <td align="center"><a href="./assets/showcase/segmentation/GCG/20260630-201826.webp"><img height="240" alt="grounded conversation generation segmentation case 3" src="./assets/showcase/segmentation/GCG/20260630-201826.webp"></a></td>
    <td align="center"><a href="./assets/showcase/segmentation/GCG/20260630-202213.webp"><img height="240" alt="grounded conversation generation segmentation case 4" src="./assets/showcase/segmentation/GCG/20260630-202213.webp"></a></td>
  </tr>
</table>

</details>

<details>
<summary>인터랙티브 세그멘테이션</summary>

<table align="center">
  <tr>
    <th align="center" colspan="2">Point Prompt</th>
  </tr>
  <tr>
    <td align="center"><a href="./assets/showcase/segmentation/inter/point_prompt_1.webp"><img height="220" alt="interactive segmentation point prompt case 1" src="./assets/showcase/segmentation/inter/point_prompt_1.webp"></a></td>
    <td align="center"><a href="./assets/showcase/segmentation/inter/04_sample_000151_000000491497_point.webp"><img height="220" alt="interactive segmentation point prompt case 2" src="./assets/showcase/segmentation/inter/04_sample_000151_000000491497_point.webp"></a></td>
  </tr>
  <tr>
    <th align="center">Box Prompt</th>
    <th align="center">Scribble Prompt</th>
  </tr>
  <tr>
    <td align="center"><a href="./assets/showcase/segmentation/inter/05_sample_000071_000000480985_point.webp"><img height="220" alt="interactive segmentation box prompt case 1" src="./assets/showcase/segmentation/inter/05_sample_000071_000000480985_point.webp"></a></td>
    <td align="center"><a href="./assets/showcase/segmentation/inter/20260630-145454.webp"><img height="220" alt="interactive segmentation scribble prompt case 1" src="./assets/showcase/segmentation/inter/20260630-145454.webp"></a></td>
  </tr>
</table>

</details>

## 데이터 프로토콜

SenseNova-Vision은 다양한 컴퓨터 비전 어노테이션을 공통 지시문-응답 스키마로 변환합니다. 각 샘플은 하나 이상의 시각 입력, 작업과 출력 규칙을 정의하는 자연어 지시문, 그리고 텍스트, 이미지 또는 텍스트-이미지 혼합 응답으로 표현되는 디코딩 가능한 타깃을 포함합니다.

<p align="center">
  <a href="./assets/fig4_training_data.webp"><img src="./assets/fig4_training_data.webp" alt="Representative SenseNova-Vision data protocol examples" width="900"></a>
</p>

## ✒️ 인용

SenseNova-Vision이 유용하다면 기술 보고서를 인용해 주세요.

```bibtex
@misc{sensenova2026sensenovavision,
      title={Vision as Unified Multimodal Generation}, 
      author={Xiaoyang Han and Jianhua Li and Kewang Deng and Zukai Chen and Xuanke Shi and Sihan Wang and Boxuan Li and Linyan Wang and Siyi Xie and Xin You and Jinsheng Quan and Zhongang Cai and Haiwen Diao and Ziwei Liu and Lei Yang and Dahua Lin and Quan Wang},
      year={2026},
      eprint={2607.06560},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2607.06560}, 
}
```

## 라이선스

이 프로젝트는 [Apache 2.0 License](./LICENSE)에 따라 공개됩니다.
