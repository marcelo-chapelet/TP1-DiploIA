# Trabajo Práctico N° 1: Análisis Exploratorio de Datos (EDA)
**Asignatura:** Diplomatura en Inteligencia Artificial  
**Estudiante:** Abel Marcelo Chapelet  

## 1. Objetivo del Trabajo
Realizar un Análisis Exploratorio de Datos (EDA) de los registros de exportaciones agricolas de Argentina
## 2. Contexto del Dataset
El dataset bajo correponde al registro nacional de **Declaraciones Juradas de Venta al Exterior (DJVE)** provisto por la Secretaría de Agricultura, Ganadería y Pesca de la República Argentina. son **80.000 observaciones** y **11 atributos cualitativos y cuantitativos** que representan transacciones de exportación de commodities y subproductos del sector agroindustrial entre los años 2023 y 2026.

## 3. Diccionario de Datos
* `id_declaracion` (Numérico Entero): Identificador unívoco de la operación aduanera.
* `fecha_venta` (Temporal / Datetime): Fecha exacta del registro y consolidación de la venta.
* `producto` (Categórico Nominal): Tipo de grano o subproducto comercializado (ej. Soja, Trigo, Aceite).
* `puerto_salida` (Categórico Nominal): Estación portuaria argentina encargada del despacho de la carga.
* `pais_destino` (Categórico Nominal): Destino internacional final del embarque.
* `via_transporte` (Categórico Nominal): Modo logístico principal utilizado (Marítima, Fluvial, Terrestre).
* `toneladas` (Numérico Continuo): Volumen total físico de la mercadería declarada.
* `requiere_refrigeracion` (Binario / Categórico): Flag indicador (1 = Requiere cadena de frío, 0 = No requiere).
* `canal_aduana` (Categórico Ordinal): Canal de inspección asignado por AFIP/Aduana (Verde, Naranja, Rojo).
* `precio_fob_usd_ton` (Numérico Continuo): Precio Free On Board unitario en dólares estadounidenses por tonelada.
* `valor_total_usd` (Numérico Continuo): Monto económico bruto de la transacción financiera (`toneladas` * `precio_fob_usd_ton`).

## 4. Metodología Aplicada
1.  **Ingesta e Integridad:** Carga de los datos y evaluación inicial de dimensiones y tipos estructurales.
2.  **Calidad de Datos:** Remoción dirigida de registros duplicados e imputación estratégica de valores nulos (NaN) mediante medidas de tendencia central (Moda) para preservar la distribución de las variables categóricas.
3.  **Feature Engineering:** Descomposición temporal de la variable cronológica en descriptores derivados (año, mes, trimestre) para capturar dinámicas estacionales de mercado.
4.  **Visualización Avanzada:** Confección de histogramas con aproximaciones KDE para formas de distribución, diagramas de caja para detección de outliers, gráficos de dispersión e identificación de correlaciones multivariadas.

## 5. Conclusiones y Hallazgos Relevantes (Validación de Hipótesis)
* **H1 (Estacionalidad) - RECHAZADA:** Los niveles volumétricos agregados se mantuvieron estables entre trimestres a raíz de la diversificación de cultivos simulados (cosecha fina y gruesa balanceadas).
* **H2 (Comportamiento de Precios) - RECHAZADA:** El análisis del Scatterplot determinó que el precio unitario se rige estrictamente por la naturaleza intrínseca del commoditie y fluctuaciones macroeconómicas, y no se altera por economías de escala basadas en el volumen unitario de la DJVE.
* **H3 (Concentración Portuaria) - CONFIRMADA:** Los nodos logísticos de 'Rosario (San Lorenzo)' y 'Rosario (San Martín)' acaparan de forma conjunta el 70% del valor FOB total movilizado, ratificando la centralidad del Gran Rosario en el esquema agroexportador argentino.
* **H4 (Destinos) - CONFIRMADA:** El volumen físico bruto es absorbido primordialmente por las demandas asiáticas (China e India), posicionándose como socios estratégicos estables del mercado nacional.