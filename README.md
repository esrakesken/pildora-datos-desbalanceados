# Manejo de datos desbalanceados · Handling Imbalanced Data

Píldora del bootcamp de IA de Factoría F5 Barcelona · **12/11/2026** · Esra Kesken

## ¿De qué trata? · What is it about?

**ES:** Cuando una clase es muy rara (fraudes, enfermedades, piezas defectuosas), un modelo puede tener un 98 % de accuracy y no detectar ni un solo caso. En esta píldora vemos por qué pasa, qué métricas mirar y cuatro técnicas para solucionarlo.

**EN:** When one class is rare (fraud, disease, defective parts), a model can be 98 % accurate and still miss every single case. This session shows why it happens, which metrics to use and four techniques to fix it.

## Qué vas a aprender

- Por qué la **accuracy** engaña con datos desbalanceados.
- **Precision, recall y F1**, y la matriz de confusión.
- Cuatro técnicas: `class_weight`, **undersampling**, **SMOTE** y **ajuste del umbral**.
- La trampa más común: hacer SMOTE **antes** del split (data leakage).

## Resultados · Results

Dataset sintético (`make_classification`): 10.000 transacciones, ≈ 1,5 % de fraudes. Regresión logística.

| Técnica | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|
| Modelo tonto (siempre "normal") | 0,985 | 0,000 | 0,000 | 0,000 |
| Baseline (sin tratar) | 0,985 | 0,000 | 0,000 | 0,000 |
| `class_weight='balanced'` | 0,685 | 0,030 | 0,659 | 0,058 |
| Undersampling | 0,646 | 0,030 | 0,727 | 0,057 |
| SMOTE | 0,697 | 0,030 | 0,636 | 0,058 |
| Umbral 0,03 | 0,906 | 0,072 | 0,455 | 0,125 |

La accuracy más alta es la del modelo que **no detecta nada**.

## Estructura

```
├── notebooks/
│   └── 01-demo.ipynb      # demo de la píldora
├── requirements.txt
└── README.md
```

## Cómo ejecutarlo · How to run

```bash
git clone https://github.com/esrakesken/pildora-datos-desbalanceados.git
cd pildora-datos-desbalanceados
python3 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/01-demo.ipynb
```

> **Mac:** si al descargar los datos sale `CERTIFICATE_VERIFY_FAILED`, ejecuta una vez el instalador de certificados de Python:
> `open "/Applications/Python 3.12/Install Certificates.command"` (cambia `3.12` por tu versión).

## Tecnologías

Python 3.12 · scikit-learn · imbalanced-learn · pandas · matplotlib

## Recursos

- [imbalanced-learn](https://imbalanced-learn.org/)
- [scikit-learn: métricas de clasificación](https://scikit-learn.org/stable/modules/model_evaluation.html#classification-metrics)
- Chawla et al. (2002), *SMOTE: Synthetic Minority Over-sampling Technique*
