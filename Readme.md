INFORME

WALDIR RODRIGUEZ

Resumen ejecutivo — hallazgos principales (extracto del informe)
Balance de clases

La tasa de churn es ~25.7%, es decir, hay cierta desbalance pero no extremadamente pronunciado. No apliqué SMOTE automáticamente porque la proporción no fue menor del umbral por defecto (15%). Si quieres que force un balance con SMOTE para comparar, lo hago.

Desempeño de los modelos (conjunto de prueba)

Las métricas principales (accuracy, precision, recall, F1 y AUC) aparecen en metrics_summary.csv. Revisa ese archivo para números exactos. En el informe encontrarás las matrices de confusión y las curvas ROC para ambos modelos.

Variables más importantes

Generé dos listados (Regresión Logística y Random Forest). Los ficheros feature_importance_logistic.csv y feature_importance_rf.csv contienen las variables y sus coeficientes/importancias.

En el informe se listan las 10 variables más influyentes por cada modelo. Estas muestran qué características incrementan o reducen la probabilidad de cancelación.

Patrones exploratorios

Si existía una columna de “tenure” (tiempo de contrato) o similar, se hizo un boxplot comparando clientes que cancelaron vs activos (boxplot_TenureMonths.png).

Si existía una columna de gasto (ej. monthly charge / total charges), se hizo un scatter para ver la relación con churn (scatter_MonthlyFee.png).

La matriz de correlación (correlation_heatmap.png) te ayuda a identificar variables numéricas altamente correlacionadas entre sí y con la cancelación.

Overfitting / Underfitting

En el informe comparo la exactitud en train vs test para cada modelo y doy recomendaciones (regularización, poda, más datos, ajuste de hiperparámetros) si detecto gap notable.

Recomendaciones de retención (generadas a partir de las variables más importantes)
(En el informe están detalladas; aquí va un resumen de las acciones más prácticas)

Si la duración del contrato (tenure / contract) aparece entre las variables top y está asociada positivamente al churn en clientes con contratos mes a mes:

Ofrecer incentivos para migrar a contratos a 12/24 meses (descuentos, meses gratis).

Programas de onboarding y atención proactiva en los primeros 90 días.

Si cargos elevados (monthly charges / total charges) se asocian con mayor churn:

Crear planes más flexibles o bundles.

Ofrecer descuentos o planes personalizados para clientes con facturas altas.

Recordatorios y opciones de pago para evitar sorpresas en la facturación.

Si satisfacción, quejas o soporte aparecen importantes:

Mejorar tiempos de respuesta y resolución en soporte técnico.

Ofrecer compensaciones/bonificaciones a clientes afectados por incidentes.

Si método de pago o problemas de facturación impactan:

Facilitar métodos alternativos y recordatorios (SMS/Email), y automatizar re-intentos de pago.

Acciones de marketing directo:

Campañas de retención dirigidas a segmentos de riesgo (crear listados desde predictions_test.csv con probabilidad alta de churn).

Test A/B de ofertas: por ejemplo, ensayo de 10% off vs mes gratis para ver qué reduce churn en cada segmento.
