# Resumo – YOLO vs CNNs

## 1. Classificação vs Detecção de Objetos

* **Classificação (CNNs clássicas):** A rede recebe uma imagem e prevê uma única classe (ex.: “gato” ou “cachorro”).
* **Detecção de Objetos (YOLO):** Além da classe, a rede também prevê **localização** (caixas delimitadoras *bounding boxes*) de múltiplos objetos na imagem.

---

## 2. Princípio do YOLO

* **YOLO = You Only Look Once**
* Divide a imagem em uma **grade (grid)**.
* Para cada célula da grade, a rede prevê:

  * Presença de objeto.
  * Coordenadas da caixa delimitadora.
  * Classe do objeto.
* Tudo é feito em **uma única passada** (rápido, tempo real).
* Diferença de métodos tradicionais: outros algoritmos usam múltiplas janelas de busca, o YOLO unifica.

---

## 3. Métricas Principais

* **Precision:** Quantos dos objetos detectados estavam corretos.
* **Recall:** Quantos dos objetos existentes foram de fato detectados.
* **F1 Score:** Combina precision e recall.
* **mAP\@0.5:** Média de precisão para sobreposição (IoU ≥ 0.5).
* **mAP@\[0.5:0.95]:** Média considerando vários limiares de IoU (mais exigente, usado em benchmarks).

---

## 4. Conceitos Importantes

* **Overfitting:** Rede aprende demais os dados de treino, não generaliza.
* **Underfitting:** Rede não consegue aprender o padrão, desempenho ruim.
* **Data Augmentation:** Transformações (flip, crop, brilho, ruído) para aumentar diversidade dos dados.
* **Transfer Learning:** Usar pesos pré-treinados (ex.: YOLOv5 pré-treinado no COCO) e adaptar para sua tarefa.

---

## 5. Exemplos Práticos

1. **YOLO (detecção):**

   * Rodar `detect.py --weights best.pt --source image.jpg`
   * Saída: imagem anotada com caixas delimitadoras.
2. **CNN simples (classificação):**

   * Treinar rede em 2 classes por poucas épocas.
   * Observar logs de `loss` e `accuracy` no treinamento.

---

## 6. Diferenças YOLO vs CNNs

| Aspecto   | CNNs (clássicas)                 | YOLO                                          |
| --------- | -------------------------------- | --------------------------------------------- |
| Tarefa    | Classificação de imagem          | Detecção de múltiplos objetos                 |
| Saída     | Uma classe por imagem            | Classes + coordenadas de caixas               |
| Estrutura | Extração de features + FC        | Backbone CNN + cabeçalho de predição por grid |
| Aplicação | Identificar "o que" há na imagem | Identificar "o que" e "onde"                  |

---

## 7. Métricas recomendadas para o projeto

* **Detecção:** mAP\@0.5 e mAP@\[0.5:0.95] (comparação padronizada).
* **Classificação:** Accuracy, Precision, Recall, F1.
* Justificativa: mAP mede a qualidade das **caixas** e das **classes** ao mesmo tempo; accuracy isolada não é suficiente.

---

## 8. Fontes sugeridas

* [YOLOv5 GitHub](https://github.com/ultralytics/yolov5)
* [Curso CNNs Stanford CS231n](http://cs231n.stanford.edu/)

---

## 9. Aprendizados-Chave

1. YOLO é uma abordagem de **detecção em tempo real** com grade única.
2. Métricas adequadas (mAP, Precision/Recall) são essenciais para comparar modelos.
3. **Transfer learning** acelera projetos e evita overfitting quando os dados são limitados.

---


