# Documentación del proceso de recolección de datos del conjunto de bank_dataset.CSV
## 1. Fuente

**Identificación de fuentes:**
- Base de datos de llamadas interna del CRM del Banco

**Descripción de la fuente:**
- Los datos están relacionados con campañas de marketing directo de una institución bancaria portuguesa. Las campañas de marketing se basaron en llamadas telefónicas. A menudo, se requirió más de un contacto con el mismo cliente, para acceder si el producto (depósito a plazo bancario) sería ('sí') o no ('no') suscrito. La base de datos contiene información personal de los clientes, como tambien el portafolio de productos actual con el banco y la gestion realizada por parte del equipo comercial y tambien si a tomado o no el producto de deposito a termino objeto de analisis, esta información fue relecolectada por el departamento de IT mediante una API.
  
## 2. Metodo de recolección de datos

**Procedimientos y herramientas:**
- Exportación programada en CSV, Almacenada diariamente en el repositorio de Github de la empresa con la supervisión del departamento de IT.

**Frecuencia de recolección:**
- Diaria
  
**Scripts de Descarga:**

```python

import pandas as pd

csv_url = "https://github.com/ITACADEMYprojectes/projecteML/blob/e8d1aab0a24ddf55af9dfd9e83b1ea79e34c1af9/bank_dataset.CSV"
df = pd.read_csv(csv_url)
print(df.info())

```

## 3. Formato y estructura de los datos

**Tipos de datos:**
- Numericos: `age`, `balance`, `day`, `month`, `duration`, `pdays`, `previous`
- Categoricos: `job`, `marital`, `education`, `default`, `housing`, `loan`, `contact`, `campaign`, `poutcome`, `deposit`


**Formato de almacenamiento:**
- Datos tabulares almacenados en formato csv.

## 4. Limitación de los datos

- Diferentes tiempos de actualización: Los datos de uso de la app y del sitio web pueden ser recolectados y actualizados en el CRM en momentos diferentes.

## 5. Consideracions sobre Dades Sensibles

**Tipos de datos sensibles:**
- Información Personal Identificable (PII): `age`, `balance`,`contact`
- Información Financera Sensible: `balance`
- Datos Comportamentales Sensibles: `housing`, `loan`

**Medidas de protección:**
- **Anonimización y Pseudonimización:**
  - Se aplicará hash para el contacto y datos sensibles como marital
- **Acceso restringido:**
  - Se restringirá el acceso unicamente al personal de la empresa implicado en al toda de decisiones
- **Cumplimiento de regulación:**
  - Cumplimiento con la GDRP
