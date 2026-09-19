# Sistema de Visão Computacional para Auditoria de Gôndola (Varejo)

Projeto de pós-graduação (Visão Computacional e Reconhecimento de Padrões) para detecção e segmentação de produtos em prateleiras de varejo, usando o dataset SKU-110K.

## Estrutura do repositório

```
notebook/   notebook Colab executável (Fases 1 a 4)
docs/       relatório técnico completo (PDF)
figuras/    figuras usadas no relatório
```

## Dataset

SKU-110K (Goldman et al., *Precise Detection in Densely Packed Scenes*, CVPR 2019).
Repositório oficial: https://github.com/eg4000/SKU110K_CVPR19

## Como reproduzir

**Visualização do notebook:** o GitHub não exibe o notebook executado direto na página (arquivo grande). Para ver as saídas: [abrir no nbviewer](https://nbviewer.org/github/lramosc1512/visao-computacional-varejo/blob/main/notebook/varejo_deteccao_segmentacao.ipynb) ou [abrir no Google Colab](https://colab.research.google.com/github/lramosc1512/visao-computacional-varejo/blob/main/notebook/varejo_deteccao_segmentacao.ipynb).

1. Abrir `notebook/varejo_deteccao_segmentacao.ipynb` no Google Colab.
2. Rodar com runtime **None** até a Fase 2 (as Fases 1 e 3 não dependem de GPU).
3. A partir da Fase 2, trocar o runtime para GPU (T4) e executar novamente a célula de Setup.
4. A Fase 3 depende de anotação manual das 28 imagens do Subconjunto B, feita externamente no Roboflow (Instance Segmentation), não incluída neste repositório.
5. A Fase 4 depende de dois vídeos de prateleira real (.mp4), enviados manualmente ao Google Drive antes de rodar a célula de inferência em vídeo.
6. Todo o cache de dados (imagens, anotações, pesos treinados) é mantido no Google Drive do usuário. A primeira execução baixa o dataset completo (~13,6 GB); execuções seguintes reutilizam o cache.

## Resultados principais

| Modelo | mAP50 (teste) | mAP50-95 (teste) | IoU médio (teste) |
|---|---|---|---|
| Detecção (YOLO26n) | 0,820 | 0,471 | 0,793 |
| Segmentação (YOLO26n-seg, v2) | 0,345 | 0,173 | - |

Metodologia completa, hiperparâmetros e análise de erros: `docs/relatorio_tecnico.pdf`.

## Uso de IA generativa

Claude (Anthropic) foi usado como assistente de codificação e redação ao longo do projeto. Declaração completa em `docs/relatorio_tecnico.pdf`, seção 7.
