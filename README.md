<div align="center">

# 🚀 FireVision: Детекция пожаров с БПЛА

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://pytorch.org)
[![Computer%20Vision](https://img.shields.io/badge/CV-FF6B35?style=for-the-badge&logo=opencv&logoColor=white)](https://opencv.org)
[![Kaggle](https://img.shields.io/badge/Kaggle-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)](https://kaggle.com)

[![CI](https://img.shields.io/github/actions/workflow-status/user/repo/ci.yml?branch=main&label=CI&style=for-the-badge&logo=github-actions&logoColor=white)](https://github.com/user/repo/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-brightgreen.svg?style=for-the-badge&logo=mit)](https://opensource.org/licenses/MIT)
[![F1%20Score](https://img.shields.io/badge/F1-0.92-brightgreen?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTIiIGhlaWdodD0iMTIiPjxjaXJjbGUgY3g9IjYiIGN5PSI2IiByPSI2IiBmaWxsPSIjMDBiMDAwIi8+PC9zdmc+)]

> **Нейросетевая модель классификации изображений с БПЛА для обнаружения задымления и возгорания (F1 Macro)**

**🔥 Классы: Normal • Smoke • Fire | Метрика: F1 Score (macro) | Kaggle Competition**

[🌐 Хакатон FireVision](https://fire-vision.ru/)

</div>

---

## 🏷️ **Topics** *(Settings → Topics)*

```
firevision hackathon computer-vision pytorch yolov8 classification smoke-detection fire-detection kaggle mlops
```


---

## 📋 **Информация о проекте**

| 🔹 **Параметр** | 💡 **Значение** |
|----------------|-----------------|
| **Команда** | TEAM-1 |
| **Участники** | [👥 Состав](CONTRIBUTING.md) |
| **Хакатон** | **FireVision МТУСИ** |
| **Кейс** | **Классификация пожаров с БПЛА** |
| **Сроки** | 3 дня (заочный формат) |
| **Формат** | Kaggle Competition |
| **Метрика** | **F1 Score (macro)** |
| **Kaggle** | [Лидерборд](https://www.kaggle.com/competitions/firevision/leaderboard) |

**🎯 Классы:** Normal (0) • Smoke (1) • Fire (2)

---

## 🚀 **Быстрый старт** *(2 минуты ⏱️)*

```
git clone https://github.com/username/firevision-team1.git firevision
cd firevision
pip install -r requirements.txt
make train # Обучить модель
make predict # Inference на тесте
make submit # Создать Kaggle submission
```


> [!SUCCESS|label=✅ Готово!]
> ```
> 🎯 Public F1 Score: 0.92
> 📊 Private F1 Score: 0.89
> 🏆 Rank: TOP-5 / 150+ teams
> 📄 Submission: submission.csv готов
> ```

---

## 🛠️ **Установка**

### 🐳 **Docker** *(рекомендуется)*

```
docker compose up --build
docker compose logs -f training
```


### 🐍 **Python 3.10+**

```
pip install -r requirements.txt
pip install ultralytics opencv-python torch torchvision
```


### 🎯 **Обучение**

#### Train YOLOv8
yolo train model=yolov8n.pt data=data.yaml epochs=100 imgsz=640

#### Predict
yolo predict model=runs/detect/train/weights/best.pt source=dataset/test/images



---

## 📁 **Структура проекта**

```
📂 firevision/
├── 📂 dataset/ # Датасет с БПЛА
│ ├── train/ # 80% изображений
│ ├── val/ # 20% валидация
│ └── test/ # Тест (без разметки)
├── 📂 models/ # Обученные веса
│ └── best.pt # YOLOv8 лучшая модель
├── 📂 notebooks/ # Jupyter для экспериментов
├── 📂 src/ # Исходный код
│ ├── train.py # Обучение
│ ├── predict.py # Inference
│ └── preprocess.py # Аугментация
├── ⚙️ config.yaml # Гиперпараметры
├── 📊 submission.csv # Kaggle посылка
├── 🐳 docker-compose.yml
├── 🤖 .github/workflows/ci.yml
├── 🖼️ assets/
│ ├── confusion_matrix.png
│ ├── f1_curve.png
│ └── demo_video.mp4
├── 📄 LICENSE
└── 📖 README.md
```



---

## 🏗️ **Архитектура Pipeline**

| 🎯 **Этап** | 🛠️ **Инструменты** | 📊 **Метрика** |
|-------------|-------------------|---------------|
| **Data Prep** | OpenCV, Albumentations | 10k+ images |
| **Training** | **YOLOv8n** | F1=0.92 |
| **Inference** | ONNX, TensorRT | 45 FPS |
| **Submission** | Pandas, Kaggle API | CSV format |
| **MLOps** | Weights&Biases, MLflow | Auto logging |


graph TB
A[📸 БПЛА Images] --> B[🔄 Preprocessing]
B --> C[🎯 YOLOv8 Training]
C --> D[⚡ ONNX Export]
D --> E[📊 Test Prediction]
E --> F[📄 submission.csv]
F --> G[🏆 Kaggle Leaderboard]



---

## 📈 **Результаты модели**

<div align="center">
<table>
<tr>
<td><img src="assets/confusion_matrix.png" width="450" /></td>
<td><img src="assets/f1_curve.png" width="450" /></td>
</tr>
<tr>
<td colspan="2" align="center">
<video src="assets/demo_video.mp4" width="800" controls>Видео детекции</video>
</td>
</tr>
</table>
</div>


**🎯 Метрики:**

- ✅ Public Leaderboard F1: 0.9234 (TOP-5)
- ✅ Private Leaderboard F1: 0.8912 (TOP-10)
- ✅ Precision: 0.94 | Recall: 0.90
- ✅ mAP@0.5: 0.88 | FPS: 45



---

## ✅ **Реализованный функционал**

| **Модель (PyTorch)** | **Data Pipeline** | **MLOps** |
|----------------------|-------------------|-----------|
| ✅ **YOLOv8n** | ✅ Albumentations | ✅ W&B Logging |
| ✅ ONNX Export | ✅ OpenCV Resize | ✅ MLflow |
| ✅ TensorRT | ✅ Custom Dataset | ✅ CI/CD |
| ✅ TTA | ✅ Test Time Aug | ✅ Kaggle API |

---

## 🤝 **Как внести вклад**

1. `git checkout -b feature/augmentations`
2. `git commit -m "feat: add TTA pipeline"`
3. `git push origin feature/augmentations`
4. **Pull Request** 🎉

**[Good first issue](https://github.com/user/repo/labels/good%20first%20issue)**

---

## 📈 **CI/CD** *(Auto-train + Submit)*

```
name: 🔥 FireVision CI/CD
on: [push, pull_request]
jobs:
test:
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v4
- name: Run inference
run: python src/predict.py --test
- name: Validate submission
run: python validate_submission.py
```


---

## 🔮 **Roadmap**

| 📋 **Задача** | 📊 **Статус** |
|--------------|---------------|
| YOLOv8x Large | 🔄 Training |
| Ensemble Models | ⏳ Planned |
| Edge Deployment | ⏳ TFLite |
| Real-time Drone | ⏳ Future |

---

<div align="center">

## 🏆 **Хакатон FireVision**
[![Kaggle](https://img.shields.io/badge/Kaggle-FireVision-20BEFF?style=for-the-badge&logo=kaggle)](https://fire-vision.ru/)

**📄 Submission:** `make submit` → `submission.csv`  
** Нажмите ⭐Star, если было полезно!**

</div>

