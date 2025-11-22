# Clustering de Acciones Samsung (2008-2019) - K-Means

Agrupación no supervisada de días de trading usando **Precio de Cierre** y **Volumen**.

## Resultados finales
- Algoritmo: **K-Means**
- Número óptimo de clusters: **3**
- Silhouette Score: **0.452**
- Davies-Bouldin: **0.781**

### Interpretación de los clusters
- **Cluster 0** → Precio bajo + volumen medio-alto → años 2008-2013 (crisis y recuperación)
- **Cluster 1** → Precio alto + volumen bajo → años 2017-2019 (Samsung en su máximo histórico)
- **Cluster 2** → Volumen extremadamente alto → días de eventos importantes

## Archivos
- `samsung.csv` → dataset original
- `samsung_clustering.ipynb` → notebook completo con análisis y optimización
- `best_kmeans_model.pkl` → modelo entrenado listo para usar

## Uso rápido del modelo
```python
import joblib
from sklearn.preprocessing import StandardScaler

modelo = joblib.load('best_kmeans_model.pkl')
scaler = joblib.load('scaler.pkl')  # (si guardas el scaler)

nuevo_dia = scaler.transform([[45000, 12000000]])
cluster = modelo.predict(nuevo_dia)
print("Pertenece al Cluster:", cluster[0])
