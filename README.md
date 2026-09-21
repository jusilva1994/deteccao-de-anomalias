# Detecção de Anomalias em Transações de Cartão de Crédito

Este projeto tem como objetivo aplicar técnicas de **machine learning** para identificar transações fraudulentas em um dataset altamente desbalanceado. Foram explorados diferentes métodos de pré-processamento, balanceamento de dados e modelos de classificação, com foco em métricas adequadas para problemas de fraude, como **precision, recall e F1-score**.

---

## 📊 Métodos Utilizados

- **Pré-processamento dos dados**
  - Normalização de variáveis.
  - Separação em treino e teste.
  - Análise exploratória inicial.

- **Balanceamento de dados**
  - **SMOTE (Synthetic Minority Oversampling Technique)** para aumentar a classe minoritária (fraudes).
  - Testes com `class_weight="balanced"` em modelos lineares e de árvores.

- **Modelos de classificação**
  - **Regressão Logística**  
    - Testada com e sem balanceamento.  
    - Recall alto após SMOTE, mas precisão baixa.  
  - **Random Forest Classifier**  
    - Melhor equilíbrio entre recall e precisão.  
    - Permite análise de importância das variáveis.  
  - **XGBoost (Extreme Gradient Boosting)**  
    - Modelo avançado com ajuste de hiperparâmetros.  
    - Obteve desempenho superior em F1-score, conciliando recall elevado com precisão mais robusta.  

- **Explicabilidade**
  - Uso de **SHAP (SHapley Additive exPlanations)** para interpretar os modelos.  
  - Identificação das variáveis mais relevantes (ex.: V10, V14, V4, Amount).  

---

## 📈 Principais Resultados

| Modelo                        | Acurácia | Precisão | Recall | F1-Score |
|-------------------------------|----------|----------|--------|----------|
| Regressão Logística + SMOTE   | ~99%     | ~0.13    | ~0.92  | ~0.23    |
| Random Forest                 | ~99%     | Melhor que logística | Recall alto | F1 equilibrado |
| XGBoost                       | ~99%     | Superior | Recall alto | **Melhor F1-score** |

---

## ✅ Conclusão

Entre os modelos testados, o **XGBoost** apresentou o **melhor desempenho geral**, alcançando um equilíbrio mais adequado entre **precisão e recall**, refletido em um F1-score superior. Isso significa que o modelo conseguiu detectar a maioria das fraudes sem gerar tantos falsos positivos quanto a regressão logística com SMOTE.  

Além disso, a análise de importância das variáveis com SHAP trouxe transparência ao processo, permitindo identificar quais características mais influenciam na detecção de anomalias.  

👉 Em aplicações reais de detecção de fraude, esse equilíbrio é fundamental: **maximizar recall para não deixar fraudes passarem despercebidas, mas também manter precisão para evitar alarmes falsos em transações legítimas**.
