# Taller 1 — Supervisión de contratación pública de bienes (SECOP II)

**MINE-4101: Ciencia de Datos Aplicada — Semestre 2026-20 — Universidad de los Andes**

## Integrantes del equipo
- Mateo Jurado
- Iván Herrera

## Objetivo
Analizar los contratos de compra de bienes (compraventa y suministros) firmados por entidades
públicas colombianas entre 2019 y 2025, extraídos de SECOP II, para ayudar a la oficina de
control interno de una entidad del Estado a **focalizar su supervisión** hacia los contratos con
mayor riesgo de desviarse del plan inicial (adición de plazo, ejecución presupuestal incompleta
o cierre sin liquidar).

## Alcance
- Entendimiento inicial de datos (dimensiones, tipos, calidad, análisis univariado del top 5 de atributos).
- Definición y justificación de una ventana de análisis apropiada dentro del rango 2019–2025.
- Construcción de 3 indicadores de desviación (plazo adicionado, no liquidado tras finalizar,
  ejecución presupuestal incompleta) y contraste de 12 hipótesis explícitas mediante pruebas
  estadísticas (chi-cuadrado, U de Mann-Whitney, Kruskal-Wallis), incluyendo tamaño de efecto
  (V de Cramér) y al menos un resultado no significativo.
- Informe ejecutivo con criterios de focalización de supervisión y limitaciones del análisis.

## Conclusiones principales (insights)
1. La **modalidad de contratación** y el **sector** son los atributos más consistentemente
   asociados a los tres tipos de desviación; **Contratación régimen especial (con ofertas)**
   tiene el peor perfil combinado (88% no liquidado, 89% ejecución incompleta).
2. Las **entidades territoriales** cierran sin liquidar con mucha más frecuencia que las
   nacionales (67.5% vs. 53.7%) — apunta a un problema de capacidad administrativa, no solo
   de control.
3. El tamaño del contrato se comporta distinto según el tipo de desviación: los contratos
   grandes se asocian más a adición de plazo; los pequeños, a cierre sin liquidar.
4. No todo hallazgo estadísticamente significativo es operacionalmente relevante — se reporta
   explícitamente el tamaño de efecto para distinguir ambos conceptos, dado el tamaño de la
   muestra (>100,000 contratos).

Ver el detalle completo de metodología, pruebas de hipótesis y recomendaciones en
[`notebooks/taller1_secop_bienes.ipynb`](notebooks/taller1_secop_bienes.ipynb).

## Organización del repositorio
```
.
├── README.md
├── requirements.txt
├── data/
│   └── secop_bienes.parquet        # dataset original provisto por el curso
└── notebooks/
    └── taller1_secop_bienes.ipynb  # notebook único, autocontenido, ejecutar en orden
```

## Instrucciones de ejecución
1. Crear un entorno virtual (opcional pero recomendado):
   ```bash
   python3 -m venv venv && source venv/bin/activate
   ```
2. Instalar dependencias:
   ```bash
   pip install -r requirements.txt
   ```
3. Abrir y ejecutar `notebooks/taller1_secop_bienes.ipynb` secuencialmente (Kernel → Restart & Run All).
   El notebook es único, no hay orden adicional que respetar.

## Dependencias
Ver `requirements.txt`. Probado con Python 3.11, pandas 2.x, scipy 1.x.

## Fuente de datos
Contratos de bienes (compraventa y suministros) firmados por entidades públicas colombianas
entre 2019 y 2025, extraídos de SECOP II (Sistema Electrónico de Contratación Pública),
provisto por el curso.
