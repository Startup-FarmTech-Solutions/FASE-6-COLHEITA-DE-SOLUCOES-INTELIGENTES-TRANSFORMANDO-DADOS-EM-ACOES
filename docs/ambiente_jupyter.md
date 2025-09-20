---

# 📌 Guia de Ambiente – Jupyter + YOLOv5

## 1. Preparar ambiente Python

No terminal:

```bash
# Criar ambiente virtual (exemplo com venv)
python -m venv pbl_fase6_env
source pbl_fase6_env/bin/activate   # Linux/Mac
pbl_fase6_env\Scripts\activate      # Windows

# Atualizar pip
pip install --upgrade pip
```

---

## 2. Instalar dependências

Crie um arquivo `requirements.txt` com versões estáveis:

```txt
torch==2.1.0
torchvision==0.16.0
opencv-python==4.8.0.76
matplotlib==3.7.3
pandas==2.0.3
```

Instale com:

```bash
pip install -r requirements.txt
```

---

## 3. Clonar YOLOv5

No terminal:

```bash
git clone https://github.com/ultralytics/yolov5.git
cd yolov5
pip install -r requirements.txt
```

---

## 4. Criar arquivo `data.yaml`

Exemplo (ajuste o caminho do dataset local):

```yaml
path: /home/seu_usuario/pbl_fase6/dataset
train: train
val: val
test: test
nc: 2
names: ['classeA','classeB']
```

---

## 5. Scripts úteis

### Treinar

```bash
python train.py --img 640 --batch 16 --epochs 50 --data data.yaml --weights yolov5s.pt --cache
```

### Detectar

```bash
python detect.py --weights runs/train/exp/weights/best.pt --img 640 --source data/images/
```

*(ajuste `--epochs` e `--batch_size` conforme sua GPU/CPU)*

---

## 6. Testar GPU (no Jupyter Notebook)

Crie uma célula:

```python
import torch
print(torch.cuda.is_available())  # True se CUDA está ativo
!nvidia-smi  # Só funciona se driver CUDA/NVIDIA instalado
```

Se não tiver GPU, roda em CPU (mais lento).

---

## 7. Dicas práticas

* Se a GPU ficar sem memória: diminua `--batch-size`.
* Sempre salve `best.pt` em uma pasta do **seu disco** (`/home/...`) e não em diretório temporário.
* No Jupyter, você pode rodar os mesmos comandos com `!` no início, ex.:

```python
!python train.py --img 640 --batch 8 --epochs 20 --data data.yaml --weights yolov5s.pt
```

---

**Entregáveis ajustados (para Jupyter):**

* `notebooks/template_jupyter.ipynb` (equivalente ao colab template, mas local).
* `requirements.txt` com versões fixas.
* `docs/ambiente_jupyter.md` explicando passo a passo (como acima).
