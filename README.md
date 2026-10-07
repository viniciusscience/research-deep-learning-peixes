# Deep Learning para classificação de peixes

Projeto acadêmico para identificação de grandes peixes migratórios capturados pela pesca oceânica brasileira, comparando CNN própria, ResNet50 e ConvNeXtTiny.

[![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/viniciusscience/research-deep-learning-peixes/blob/main/Trabalho_Final_DL_Peixes_CNN_ResNet50_ConvNeXtTiny.ipynb)

## Modelos e protocolo

| Modelo | Estratégia |
| --- | --- |
| CNN própria | Treinamento do zero (baseline) |
| ResNet50 | Transfer learning e fine-tuning com pesos ImageNet |
| ConvNeXtTiny | Transfer learning e fine-tuning com pesos ImageNet |

Imagens RGB de 224 × 224, batch de 32, seed 123 e split estratificado de 70% treino, 15% validação e 15% teste. O pipeline inclui data augmentation e pesos de classe.

A avaliação inclui Accuracy, Precision, Recall, F1, Top-3, matrizes de confusão, ROC-AUC/PR-AUC, McNemar, bootstrap, custo computacional e Grad-CAM.

## Execução

1. Abra o notebook no Colab e ative um runtime com GPU.
2. Monte seu Google Drive.
3. Ajuste `CANONICAL_ROOT` para seu dataset, contendo `images/` e `metadata_imagens.csv`.
4. Execute as células na ordem. As saídas são gravadas em `MODEL_DIR`.

O CSV requer `especie`, `arquivo_local`, `fonte` e `licenca`. Os caminhos em `arquivo_local` são relativos à raiz do dataset.

Raiz configurada: `/content/drive/MyDrive/dataset_peixes_inaturalist_completo/dataset_peixes_inaturalist`.

Dependências: TensorFlow/Keras, NumPy, pandas, Matplotlib, scikit-learn e SciPy. Esta publicação não fixa versões; o ambiente foi preparado para Colab.

## Resultados e dados

Esta cópia contém resultados piloto históricos, mas não inclui as saídas completas da comparação final. Os resultados históricos usam split anterior 80/20 e devem ser analisados separadamente do protocolo 70/15/15.

A execução exporta métricas, checkpoints, manifest do split, figuras e um marcador `RUN_COMPLETE.json` quando os arquivos esperados estão presentes.

O Grad-CAM é uma análise qualitativa complementar; a implementação genérica pode exigir adaptação para backbones aninhados conforme a versão do Keras.

Imagens, metadados e modelos treinados são externos ao repositório. As fontes incluem iNaturalist, GBIF e Wikimedia Commons; consulte a licença e a atribuição de cada imagem antes de redistribuí-la.

## Autor

[Vinícius — viniciusscience](https://github.com/viniciusscience)
