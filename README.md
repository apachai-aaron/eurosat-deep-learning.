# EuroSAT — Clasificación de imágenes satelitales con CNN

Proyecto individual de Deep Learning utilizando **TensorFlow + Keras**.

## Problema

Clasificación multiclase de imágenes satelitales RGB en diez clases de cobertura/uso del suelo mediante redes neuronales convolucionales (CNN).

## Dataset

- **EuroSAT RGB**, imágenes satelitales Sentinel-2.
- 27,000 imágenes, resolución de 64 × 64, tres canales RGB, 10 clases.
- **Fuente:** https://www.tensorflow.org/datasets/catalog/eurosat
- **Repositorio original:** https://github.com/phelber/eurosat
- Los datos se descargan **automáticamente** desde el notebook. No hay necesidad de almacenarlos en GitHub.

## Contenido

| Archivo | Función |
|---|---|
| `EuroSAT_Clasificacion_CNN.ipynb` | Reporte completo: datos, dos CNN, validación, comparación, prueba y predicciones. |
| `modelo_final.keras` | Modelo ganador, arquitectura + pesos (**se genera al ejecutar el notebook**). |
| `metricas_finales.json` | Métricas registradas (**se genera al ejecutar el notebook**). |
| `requirements.txt` | Dependencias principales. |

## Cómo ejecutarlo

1. Abrir `EuroSAT_Clasificacion_CNN.ipynb` en **Google Colab** desde el repositorio.
2. Activar **GPU T4**, si está disponible (`Entorno de ejecución → Cambiar tipo de entorno de ejecución`).
3. Elegir **Entorno de ejecución → Ejecutar todo**. La descarga y el entrenamiento necesitan conexión y pueden tomar varios minutos.
4. Revisar las curvas de aprendizaje, resultados, matriz de confusión y conclusiones. **Completar la interpretación personal** de los resultados de la sección 6 antes de entregar.
5. En la sección 7, cambiar `DESCARGAR_ENTREGABLES = True` y ejecutar esa celda para descargar `modelo_final.keras` y `metricas_finales.json`.
6. Subir ambos archivos al repositorio, usando **Add file → Upload files** en GitHub.
7. Guardar el notebook **con sus salidas** (`Archivo → Guardar una copia en GitHub`) y comprobar que el README, notebook, modelo y métricas estén en el repositorio.
8. Entregar el enlace del repositorio en Canvas.

> El archivo `.keras` **no está incluido inicialmente** porque debe generarse entrenando el modelo: de lo contrario no tendría pesos auténticos. Nunca reportar métricas que no provengan de una ejecución real.

## Metodología

- División estratificada y reproducible: 70% entrenamiento, 15% validación, 15% prueba.
- **CNN inicial:** bloques convolucionales + pooling + clasificación.
- **CNN ajustada:** data augmentation, Batch Normalization, Dropout, GlobalAveragePooling y ajuste dinámico del learning rate.
- **Selección del mejor modelo:** únicamente con validación, sin mirar el conjunto de prueba.
- **Evaluación final:** accuracy, loss, F1 macro, classification report y matriz de confusión.
- **Aplicación:** función `clasificar_imagen(ruta)` y modelo `.keras` recargable.

## Referencia

Helber, P., Bischke, B., Dengel, A., & Borth, D. (2017). *EuroSAT: A Novel Dataset and Deep Learning Benchmark for Land Use and Land Cover Classification*. arXiv:1709.00029. https://arxiv.org/abs/1709.00029
