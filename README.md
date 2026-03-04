# MNIST Handwritten Digits - MLP con scikit-learn

Clasificación de dígitos escritos a mano usando una red neuronal MLP (Multi-Layer Perceptron) con scikit-learn, entrenada en el dataset MNIST y probada con imágenes propias.

## Estructura del Proyecto

```
├── notebooks/
│   ├── 01_entrenar_modelo.ipynb        # EDA, entrenamiento y evaluación del MLP
│   ├── 02_procesar_imagenes.ipynb      # Preprocesamiento de fotos propias
│   └── 03_probar_imagenes_propias.ipynb # Prueba del modelo con imágenes propias
├── mis_imagenes/raw/                   # Fotos originales de dígitos
├── mis_imagenes_procesadas/            # Imágenes preprocesadas (28x28)
├── modelo/                             # Modelo entrenado (.pkl)
└── resultados/                         # Gráficas exportadas
```

## Cómo usar

### 1. Activar el environment
```bash
conda activate introML
```

### 2. Ejecutar notebooks en orden
1. `01_entrenar_modelo.ipynb` — Entrena el modelo
2. Colocar tus fotos en `mis_imagenes/raw/` con formato: `{digito}_{numero}.jpg` (ej: `3_01.jpg`, `7_02.jpg`)
3. `02_procesar_imagenes.ipynb` — Preprocesa las fotos
4. `03_probar_imagenes_propias.ipynb` — Prueba y visualiza resultados

## Requisitos
- Python 3.x con conda environment `introML`
- scikit-learn, matplotlib, numpy, pandas, pillow, seaborn
