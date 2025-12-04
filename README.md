## Descripción del repositorio

Este repositorio implementa una **simulación del flujo metodológico presentado en el artículo**:

> March, C., Pérez, C. y Salido, M. (2024).  
> *Developing an Algorithm Selector for Green Configuration in Scheduling Problems*.  
> arXiv:2409.08641. https://arxiv.org/abs/2409.08641

El objetivo es **reproducir la lógica del artículo** para seleccionar el solver más adecuado según las características de una instancia del Job Shop Scheduling Problem (JSSP). La implementación sigue la estructura de entrenamiento y ejecución propuesta en el trabajo original.

---

---

## Estructura del flujo metodológico

### 🔹 1. Training phase (fase de entrenamiento)

En esta fase se procesa el conjunto de instancias conocidas y se recolecta la información necesaria para entrenar el sistema de recomendación:

- **Feature processing:**  
  Cada instancia del JSSP es analizada para extraer características relevantes (features) que serán usadas como entrada del modelo.

- **Solvers considerados:**  
  Las instancias se resuelven con diferentes solvers (por ejemplo, *Gecode*, *CPLEX*, *Gurobi*) con el fin de registrar su rendimiento.

- **Entrenamiento de modelos de ML:**  
  Con las características extraídas y el desempeño obtenido por cada solver, se entrenan diferentes modelos de aprendizaje supervisado, tales como:  
  - Naive Bayes  
  - Logistic Regression  
  - Random Forest  
  - MLP  
  - XGBoost  
  - (entre otros)

El resultado de esta fase es un **modelo de recomendación** capaz de predecir qué solver es más conveniente para una nueva instancia.

---

### 🔹 2. Execution phase (fase de ejecución)

En esta fase se utiliza el sistema entrenado para recomendar el solver adecuado:

- **Nuevas instancias:**  
  El usuario proporciona una instancia no vista previamente.

- **Feature processing:**  
  La instancia es procesada para obtener sus características mediante el mismo pipeline utilizado en el entrenamiento.

- **Recommendation system:**  
  El modelo predice cuál solver debería entregar el mejor rendimiento según las características de esa instancia.

- **Best solver:**  
  El sistema devuelve la recomendación final del solver óptimo.

---

Este repositorio **imita la metodología del artículo**, reproduciendo tanto la fase de entrenamiento como la fase de recomendación, con el propósito de identificar, a partir de las características de una instancia, **el solver que ofrece el mejor desempeño esperado**.
