# 🧠 MNIST Handwritten Digits — MLP con scikit-learn

Clasificación de dígitos escritos a mano (0–9) usando una **red neuronal MLP** (Multi-Layer Perceptron) de scikit-learn, entrenada con el dataset [MNIST](http://yann.lecun.com/exdb/mnist/) y evaluada con **imágenes propias dibujadas a mano en papel**.

## Descripción

El proyecto entrena un modelo MLP con arquitectura **(784 → 128 → 64 → 10)** sobre las 70,000 imágenes del dataset MNIST. Después, se agregan 40–50 imágenes propias de dígitos escritos a mano (fotografiados desde papel) al conjunto de prueba para evaluar cómo generaliza el modelo fuera del dataset original.

### Características principales
- 📊 **EDA visual** del dataset MNIST (distribución de clases, imágenes promedio, variedad por dígito)
- 🏗️ **Entrenamiento MLP** con scikit-learn (`MLPClassifier`) — curva de pérdida, confusion matrix, predicciones correctas e incorrectas
- 📸 **Preprocesamiento automático** de fotos de dígitos en papel → formato MNIST 28×28
- 🎯 **Predicción individual** de cada imagen propia con gráfica de confianza por dígito
- 📈 **Análisis comparativo** entre accuracy en MNIST vs imágenes propias

## Estructura del Proyecto

```
mnist-handwritten-digits/
├── environment.yml                      # Conda environment (ver Instalación)
├── notebooks/
│   ├── 01_entrenar_modelo.ipynb         # EDA, entrenamiento y evaluación del MLP
│   ├── 02_procesar_imagenes.ipynb       # Preprocesamiento de fotos propias
│   └── 03_probar_imagenes_propias.ipynb # Predicciones individuales y análisis
├── mis_imagenes/
│   └── raw/                             # ← Coloca aquí tus fotos de dígitos
├── mis_imagenes_procesadas/             # Imágenes convertidas a 28x28 (generado)
├── modelo/                              # Modelo entrenado .pkl (generado)
└── resultados/                          # Gráficas exportadas en PNG (generado)
```

## Instalación

### Opción 1: Crear environment desde el archivo (recomendado)
```bash
conda env create -f environment.yml
conda activate mnist-mlp
```

### Opción 2: Instalar en un environment existente
```bash
conda activate <tu_environment>
pip install scikit-learn matplotlib numpy pandas pillow seaborn jupyterlab
```

## Cómo Usar

### Paso 1 — Entrenar el modelo
```bash
conda activate mnist-mlp
jupyter lab
```
Abre y ejecuta **`notebooks/01_entrenar_modelo.ipynb`**. Esto descarga MNIST, entrena el MLP y guarda el modelo en `modelo/`.

### Paso 2 — Preparar tus imágenes propias
Dibuja dígitos (0–9) con **marcador oscuro en papel blanco**, toma una foto de cada uno y colócalos en `mis_imagenes/raw/`.

**Convención de nombres:**
```
{dígito_real}_{número}.jpg
```
| Archivo | Dígito real |
|---------|------------|
| `3_01.jpg` | 3 |
| `3_02.jpg` | 3 |
| `7_01.jpg` | 7 |
| `0_05.jpg` | 0 |

> El primer número antes del `_` es la etiqueta real (para evaluar si el modelo acertó). Formatos soportados: `.jpg`, `.jpeg`, `.png`, `.bmp`, `.heic`, `.webp`.

**Tips para mejores resultados:**
- Un solo dígito por foto, centrado
- Buena iluminación, fotografiar de frente
- Trazo grueso y oscuro sobre fondo claro

### Paso 3 — Preprocesar las fotos
Ejecuta **`notebooks/02_procesar_imagenes.ipynb`**. Esto convierte automáticamente cada foto a escala de grises 28×28 estilo MNIST.

### Paso 4 — Probar y visualizar resultados
Ejecuta **`notebooks/03_probar_imagenes_propias.ipynb`**. Para cada imagen verás:
- La foto original vs. la versión procesada
- La predicción del modelo con barra de confianza por dígito (✅/❌)
- Resumen final con grid de todas las predicciones, confusion matrix y accuracy por dígito

Todas las gráficas se guardan automáticamente en `resultados/` a 150 dpi.

## Tecnologías

| Herramienta | Uso |
|---|---|
| **scikit-learn** | `MLPClassifier` — red neuronal MLP |
| **matplotlib** / **seaborn** | Visualizaciones y gráficas |
| **Pillow** | Procesamiento de imágenes |
| **NumPy** / **Pandas** | Manejo de datos |
| **JupyterLab** | Entorno de desarrollo interactivo |

## Resultados Esperados

El modelo MLP (128, 64) típicamente alcanza **~97% accuracy** en el test set de MNIST. El accuracy en imágenes propias suele ser menor dependiendo de la calidad del preprocesamiento y la caligrafía.
