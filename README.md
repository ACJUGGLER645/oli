# Caso LogiExpress — Optimización de rutas de última milla

Proyecto académico del curso **Electiva Técnica II — Ciencia de Datos**
de la Tecnología en Desarrollo de Software (ETITC).

Se aborda el **Problema de Ruteo de Vehículos con Capacidad** (CVRP)
sobre el dataset público *Brazilian E-Commerce Public Dataset by Olist*
(Kaggle), con foco en la ciudad de São Paulo. Se construyen rutas
factibles para 30 pedidos desde un único depósito usando la fórmula de
Haversine para la matriz de distancias, *vecino más cercano* (NN) como
solución inicial y *2-opt* como refinamiento local.

## Identificación

| Campo | Valor |
|---|---|
| Programa | Tecnología en Desarrollo de Software |
| Curso | Electiva Técnica II — Ciencia de Datos |
| Institución | Escuela Tecnológica Instituto Técnico Central (ETITC) |
| Docente | Elías Buitrago |
| Integrantes | Jhon Alejandro Correal Martínez · Rafael Andrés Guzmán Rodríguez |
| Semestre | Séptimo |
| Repositorio | <https://github.com/ACJUGGLER645/oli> |
| GitHub Pages | <https://acjuggler645.github.io/oli/> |

## Resultado

- 30 pedidos seleccionados en São Paulo.
- Capacidad por vehículo: 15 kg.
- 4 rutas factibles construidas.
- Distancia total: **161,60 km** (reducción de 6,92 km respecto a la
  solución inicial entregada por NN, equivalente al 4,1 %).

## Estructura del repositorio

```
.
├── README.md                       # este archivo
├── index.html                      # versión web (GitHub Pages)
├── informe.tex                     # fuente LaTeX del informe
├── informe.pdf                     # informe técnico final
├── .gitignore
├── notebooks/
│   ├── original.ipynb              # notebook propuesto por el docente, sin ejecutar
│   ├── original_ejecutado.ipynb    # copia ejecutada del original (referencia opcional)
│   └── Optimizacion_Rutasv3.ipynb  # notebook propuesto, ejecutado de principio a fin
├── data/
│   ├── pedidos_logiexpress_limpio.csv     # 30 pedidos seleccionados
│   └── matriz_distancias_haversine.csv    # matriz 31×31 de distancias
└── assets/                         # imágenes embebidas en el informe
    ├── ETITC.png                   # marca de agua institucional
    ├── evidencia-dataset.png
    ├── tabla-pedidos.png
    ├── matriz-distancias.png
    ├── grafica-complejidad.png
    ├── grafica-distancias.png
    ├── mapa-inicial.png
    └── mapa-rutas.png
```

## Cómo ejecutar

### Notebook (entorno recomendado: Google Colab)

1. Abrir `notebooks/Optimizacion_Rutasv3.ipynb` en Google Colab.
2. Al pedir credenciales de Kaggle, cargar el archivo `kaggle.json`
   personal mediante la celda de subida que aparece al inicio.
3. Ejecutar todas las celdas (`Runtime → Run all`).
4. Las salidas (CSVs y mapas) se generan en el directorio de trabajo.

### Notebook local (Jupyter)

```bash
pip install pandas numpy folium matplotlib kagglehub
jupyter notebook notebooks/Optimizacion_Rutasv3.ipynb
```

### Compilar el informe en PDF

```bash
pdflatex informe.tex
pdflatex informe.tex   # segunda pasada para la tabla de contenidos
```

Requiere una distribución LaTeX (TeX Live, MiKTeX o MacTeX) con los
paquetes `eso-pic`, `transparent`, `tcolorbox`, `hyperref` y `babel`
(español).

### Ver la versión web localmente

```bash
python3 -m http.server 8000
# abrir http://localhost:8000 en el navegador
```

## Componentes del proyecto

| Componente | Ruta | Descripción |
|---|---|---|
| Informe técnico | `informe.pdf` / `informe.tex` | Documento principal con marca de agua institucional |
| Versión web | `index.html` | Equivalente navegable con mapa interactivo |
| Notebook original | `notebooks/original.ipynb` | Punto de partida del docente, sin modificar |
| Notebook propuesto | `notebooks/Optimizacion_Rutasv3.ipynb` | Versión modificada y ejecutada por el equipo |
| Datos limpios | `data/pedidos_logiexpress_limpio.csv` | 30 pedidos seleccionados |
| Matriz de distancias | `data/matriz_distancias_haversine.csv` | Matriz 31×31 precomputada |

## Notas sobre los notebooks

El notebook **original** se conserva tal cual fue entregado por el
docente, sin ejecutar, para mantener la trazabilidad del punto de
partida. El notebook **v3** contiene las modificaciones propuestas por
el equipo: parametrización de capacidad, criterios de selección de la
muestra, interpretación del experimento de complejidad y bloque de
informe final. La lógica algorítmica (Haversine, NN, 2-opt, sweep)
se conserva sin cambios.

## Datos utilizados

Los datos provienen del dataset público **Brazilian E-Commerce Public
Dataset by Olist** disponible en Kaggle:
<https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce>

El dataset utilizado en este proyecto es el indicado por el docente
en la guía del curso. No se introducen fuentes de datos externas.

## Licencia y uso

Material académico con fines educativos. El dataset Olist está
publicado bajo los términos definidos en Kaggle por sus autores.
