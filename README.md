# 6.-Sistemas-recomendadores


## Descripción

Este proyecto implementa y compara diferentes enfoques para construir sistemas de recomendación de películas utilizando el conjunto de datos TMDB.

El objetivo es analizar cómo distintas técnicas de recomendación producen resultados diferentes y evaluar el impacto de incorporar metadatos adicionales para mejorar la calidad de las recomendaciones.

---

# archivo credits

https://storage.googleapis.com/kaggle-data-sets/3405/6663/compressed/credits.csv.zip (189 mb, no se puede respaldar en repositorio)



---

## Tecnologías utilizadas

- Python 3
- Pandas
- NumPy
- Scikit-Learn
- Jupyter Notebook

---

## Modelos implementados

### 1. Recomendador simple

Clasifica las películas utilizando la calificación ponderada de IMDb, considerando tanto la valoración promedio como el número de votos.

---

### 2. Recomendador basado en contenido (TF-IDF)

Utiliza la sinopsis de cada película para construir una representación vectorial mediante TF-IDF y calcula la similitud utilizando la similitud del coseno.

---

### 3. Recomendador basado en metadatos

Amplía la representación de cada película utilizando:

- Actores principales
- Director
- Géneros
- Palabras clave

La información se combina en una representación textual ("soup") utilizada para calcular similitudes.

---

## Mejoras implementadas

### Filtro de popularidad

Después de obtener las películas más similares, el sistema calcula la calificación ponderada de IMDb y devuelve las películas mejor posicionadas considerando tanto similitud como popularidad.

### Incorporación de miembros del equipo

Además del director y el reparto, se incorporan guionistas y productores para enriquecer la representación de cada película.

### Mayor peso del director

El nombre del director se repite varias veces dentro de la representación textual para incrementar su influencia durante la vectorización.

En las pruebas realizadas sobre una muestra aleatoria de aproximadamente 5,000 películas (≈11 % del conjunto de datos), esta estrategia no mostró un incremento significativo en la presencia de películas del mismo director entre las recomendaciones. Este comportamiento puede atribuirse al sesgo introducido por la muestra utilizada y no necesariamente a una limitación del método.

---

## Resultados

Los experimentos muestran que:

- Los modelos basados en contenido producen recomendaciones más específicas que el recomendador simple.
- La incorporación de metadatos mejora la representación de las películas.
- El filtro híbrido reduce la aparición de películas con pocas valoraciones.
- El peso adicional del director constituye una estrategia prometedora, aunque requiere evaluarse sobre el conjunto completo para medir correctamente su impacto.

---

## Limitaciones

- El cálculo de la matriz completa de similitud para más de 45 mil películas requiere aproximadamente 15 GB de memoria RAM.
- Para las pruebas experimentales se utilizó una muestra de aproximadamente 5,000 películas para evitar problemas de memoria.
- El sistema continúa siendo un recomendador basado en contenido y no incorpora aprendizaje a partir del comportamiento de los usuarios.


