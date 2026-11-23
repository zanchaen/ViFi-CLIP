# 원본 대비 수정 사항 (Colab GPU 1대 환경)

원본: https://github.com/muzairkhattak/ViFi-CLIP
모델 구조와 학습 로직은 바꾸지 않았다.

| 파일 | 수정 내용 | 이유 |
|---|---|---|
| main.py | NVIDIA Apex → torch.cuda.amp (GradScaler, autocast) | 최신 PyTorch/Colab에서 Apex 설치 불가 |
| main.py | `--local-rank` 인자와 LOCAL_RANK 환경변수 지원 | 최신 PyTorch 실행기(torchrun) 호환 |
| main.py | 마지막 epoch 정확도를 로그에 따로 출력 | 최고값과 마지막 epoch 값을 함께 기록하기 위해 |
| datasets/build.py | num_workers 16 → 환경변수 NUM_WORKERS(기본 4) | Colab CPU 개수에 맞춤 |
| datasets/pipeline.py | np.int, np.float 등 → int, float | 최신 NumPy에서 제거된 타입 |