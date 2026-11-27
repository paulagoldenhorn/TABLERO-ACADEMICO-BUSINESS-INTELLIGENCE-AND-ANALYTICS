# Tablero de Indicadores Académicos (KPIs) para la Gestión Educativa

**Trabajo Práctico Final de BI & Analytics.**

**Aplicación desplegada:** https://tablero-academico-business-intelligence-and-analytics.streamlit.app/

## Integrantes
- Juan Ignacio Pintarelli
- Aaron Fraga
- Gastón Cuevas
- Paula Goldenhorn

## Descripción
Dashboard académico que analiza la participación, el rendimiento y la matrícula en tres asignaturas (Álgebra, Algoritmos y Estructuras de Datos, y Probabilidad y Estadística) de una plataforma educativa. Datos sintéticos.

## Estructura del proyecto

```
.
├── README.md
├── Consignas TFI.md          consigna del trabajo
├── INFORME TECNICO.pdf       informe técnico del trabajo
├── requirements.txt          dependencias de Python
├── .gitignore                archivos que no se suben (entornos, secretos, salidas generadas)
├── .streamlit/               configuración (tema) de Streamlit
│
├── data/                     datos del proyecto
│   ├── algebra/              reportes exportados de la plataforma y su versión limpia
│   ├── algoritmosestructuras/
│   ├── probabilidadestadistica/
│   ├── matriculados/         listados oficiales de matriculados
│   └── integrado/            las tres asignaturas unidas (lo que lee la aplicación)
│
├── jupyter/                  INVESTIGACIÓN
│   ├── algebra.ipynb
│   ├── algoritmosestructuras.ipynb
│   ├── probabilidadestadistica.ipynb
│   ├── matriculados.ipynb
│   ├── integracion.ipynb
│   ├── utils_limpieza.py
│   └── kpis/                 un notebook por grupo de indicadores
│       ├── calificaciones.ipynb
│       ├── participacion.ipynb
│       ├── matricula.ipynb
│       └── cruces.ipynb
│
└── src/                      APLICACIÓN (lo que se despliega)
    ├── app.py                punto de entrada y navegación
    ├── constants.py          constantes del proyecto (nombres, textos, parámetros)
    ├── .streamlit/           configuración (tema) de Streamlit
    ├── data/
    │   ├── kpis/             cálculo de los indicadores
    │   └── services/         preparan los datos que muestra cada pantalla
    └── ui/
        ├── pages/            las siete pantallas
        ├── components/       tarjetas, gráficos, tablas y filtros reutilizables
        └── theme.css         estilos
```

## Investigación (`jupyter/`)

1. **Limpieza por asignatura** (`algebra`, `algoritmosestructuras`, `probabilidadestadistica`): toman los reportes exportados de la plataforma (calificaciones, participación y trazabilidad), corrigen errores y los guardan en formato Parquet.
2. **Matriculados** (`matriculados`): consolida los listados oficiales de las tres asignaturas.
3. **Integración** (`integracion`): une todo en `data/integrado/`.
4. **Indicadores** (`kpis/`): calculan y justifican los indicadores de calificaciones, participación, matrícula y los cruces entre participación y notas.

## Aplicación (`src/`)

Lee los datos de `data/integrado/` y los muestra en siete pantallas: General, Participación, Trazabilidad, Rendimiento Académico, Notas vs Participación, Individual, y Matrícula y Alertas.

- `data/kpis/` calcula los indicadores a partir de los datos integrados.
- `data/services/` toma esos resultados y arma las tablas de cada pantalla.
- `ui/` dibuja las pantallas con Streamlit.

## Cómo ejecutar la aplicación

```bash
# Configurar entorno virtual
python -m venv env
source env/Scripts/activate

# Instalar dependencias
python -m pip install --upgrade pip
pip install -r requirements.txt

# Correr la aplicación 
streamlit run src/app.py
```

La aplicación queda disponible en http://localhost:8501.
