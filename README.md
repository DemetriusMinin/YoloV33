

```bash
git clone https://github.com/DemetriusMinin/YoloV33.git  # клонируете файлы из репозитория
cd yolov3
pip install -r requirements.txt  # скачиваете файлы и библиотеки необходимые для работы YoloV3
```

</details>

<details>
<summary>Вывод</summary>

YOLOv3 [PyTorch Hub](https://docs.ultralytics.com/yolov5/tutorials/pytorch_hub_model_loading) вывод. [Модели](https://github.com/ultralytics/yolov5/tree/master/models) загружаются автоматически из последней [версии](https://github.com/ultralytics/yolov5/releases) YOLOv3.

```python
import torch

# Модели
model = torch.hub.load("ultralytics/yolov3", "yolov3")  # или yolov5n - yolov5x6, 

# Фото
img = "https://ultralytics.com/images/zidane.jpg"  # или file, Path, PIL, OpenCV, numpy, list

# Вывод
results = model(img)

# Результаты
results.print()  # or .show(), .save(), .crop(), .pandas(), etc.
```

</details>

<details>
<summary>Вывод с помощью detect.py</summary>

`detect.py`выполняет логический вывод из различных источников, автоматически загружая модели из последней версии YOLOv3 и сохраняя результаты в `runs/detect`.

```bash
python detect.py --weights yolov5s.pt --source 0                               # камера
                                               img.jpg                         # фото
                                               vid.mp4                         # видео
                                               screen                          # скриншот
                                               path/                           # директорию
                                               list.txt                        # список изображений
                                               list.streams                    # список потоков
                                               'path/*.jpg'                    # glob модуль
                                               'https://youtu.be/LNwODJXcvt4'  # YouTube
                                               'rtsp://example.com/media.mp4'  # RTSP, RTMP, HTTP потоки
```

</details>

<details>
<summary>Тренировка</summary>

Приведенные ниже команды воспроизводят результаты [COCO](https://github.com/ultralytics/yolov5/blob/master/data/scripts/get_coco.sh). [Модели](https://github.com/ultralytics/yolov5/tree/master/models)
and [датасеты](https://github.com/ultralytics/yolov5/tree/master/data) загружается автоматически из последней  [версии](https://github.com/ultralytics/yolov5/releases) YOLOv3. Время тренировки для YOLOv5 n/s/m/l/x составляет 1/2/4/6/8 дней на GPU V100  (в несколько раз быстрее на [нескольких графических процессорах](https://docs.ultralytics.com/yolov5/tutorials/multi_gpu_training)). Используйте самый большой размер `--batch-size` возможны также, `--batch-size -1` для YOLOv3 [AutoBatch](https://github.com/ultralytics/yolov5/pull/5092). Размер партий, указаны для V100-16GB.

```bash
python train.py --data coco.yaml --epochs 300 --weights '' --cfg yolov5n.yaml  --batch-size 128
                                                                 yolov5s                    64
                                                                 yolov5m                    40
                                                                 yolov5l                    24
                                                                 yolov5x                    16
```

<img width="800" src="https://user-images.githubusercontent.com/26833433/90222759-949d8800-ddc1-11ea-9fa1-1c97eed2b963.png">

</details>
