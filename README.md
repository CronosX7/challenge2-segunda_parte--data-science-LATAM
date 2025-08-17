# Informe de Factores que Influyen en la Cancelación de Clientes

## 1. Introducción

El objetivo de este análisis fue identificar los factores más relevantes que influyen en la **cancelación de clientes**.  
Se entrenaron dos modelos basados en árboles que soportan valores faltantes:

- **Random Forest**  
- **HistGradientBoostingClassifier** (evaluado con **Permutation Importance**)  

Se calcularon las métricas de desempeño para ambos modelos y se analizaron las variables más influyentes en la predicción de cancelación.

---

## 2. Rendimiento de los modelos

| Modelo | Exactitud | Precisión | Recall | F1-score |
|--------|-----------|-----------|--------|----------|
| Random Forest | 0.7831 | 0.7699 | 0.7831 | 0.7734 |
| HistGradientBoosting | 0.7859 | 0.7739 | 0.7859 | 0.7773 |

**Análisis:**  
- Ambos modelos presentan un desempeño muy similar.  
- **HistGradientBoosting** mostró un leve mejor desempeño en todas las métricas, aunque la diferencia es mínima.  
- No se observan signos evidentes de **overfitting** ni de **underfitting**, indicando buena generalización.

---

## 3. Factores más relevantes según los modelos

### 3.1 Random Forest

Variables más importantes (top 10):

1. `account_Charges_Total` – Cargos totales del cliente.  
2. `tenure` – Tiempo que el cliente ha permanecido.  
3. `support_calls` – Número de llamadas al soporte.  
4. `contract_type` – Tipo de contrato.  
5. `monthly_charges` – Pago mensual.  
6. `service_plan` – Plan contratado.  
7. `num_complaints` – Número de quejas registradas.  
8. `internet_service` – Tipo de servicio de internet.  
9. `payment_method` – Método de pago.  
10. `customer_age` – Edad del cliente.

### 3.2 HistGradientBoosting (Permutation Importance)

Variables más importantes (top 10):

1. `account_Charges_Total`  
2. `monthly_charges`  
3. `tenure`  
4. `support_calls`  
5. `contract_type`  
6. `num_complaints`  
7. `service_plan`  
8. `payment_method`  
9. `internet_service`  
10. `customer_age`

**Observaciones:**  
- Las variables más consistentes entre ambos modelos son:  
  - `account_Charges_Total`  
  - `tenure`  
  - `monthly_charges`  
  - `support_calls`  
  - `contract_type`  
- Estas variables tienen **mayor impacto en la predicción de cancelación**.  
- Variables distintas entre modelos pueden indicar interacciones específicas que un modelo capta mejor que otro.

---

## 4. Estrategias de Retención Basadas en los Factores Identificados

1. **Cargos totales y pagos mensuales** (`account_Charges_Total`, `monthly_charges`):  
   - Analizar si los clientes con cargos altos tienen mayor riesgo de cancelación.  
   - Proponer descuentos, planes personalizados o beneficios adicionales a clientes de alto gasto.

2. **Tiempo de permanencia** (`tenure`):  
   - Detectar clientes nuevos en riesgo y ofrecer **incentivos iniciales** para aumentar su fidelidad.  
   - Mantener programas de fidelización para clientes antiguos.

3. **Llamadas al soporte y quejas** (`support_calls`, `num_complaints`):  
   - Monitorear clientes con alto número de interacciones con soporte.  
   - Mejorar la calidad del servicio al cliente y resolver problemas proactivamente.

4. **Tipo de contrato y plan de servicio** (`contract_type`, `service_plan`):  
   - Evaluar planes con mayor tasa de cancelación y ofrecer **paquetes alternativos o upgrades**.  
   - Promocionar planes que combinen valor y retención.

5. **Método de pago e información demográfica** (`payment_method`, `customer_age`):  
   - Identificar patrones que puedan afectar la continuidad del servicio.  
   - Ofrecer recordatorios de pago o métodos más convenientes para clientes en riesgo.

---

## 5. Conclusión

- Ambos modelos identifican de manera consistente los **principales factores de cancelación**.  
- Las estrategias de retención deben centrarse en **optimizar precios, mejorar la atención al cliente y personalizar planes**.  
- La información obtenida permite a la empresa tomar decisiones **data-driven** para reducir la cancelación y aumentar la fidelidad de los clientes.
