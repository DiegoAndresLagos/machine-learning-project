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
- Numericos: `age`, `balance`, `day`, `month`, `duration`, `pdays`, `previous`, ` `, ` `, ` `
- Categoricos: `job`, `marital`, `education`, `default`, `housing`, `loan`, `contact`, `campaign`, `poutcome`, `deposit`


**Format d'Emmagatzematge:**
- Dades tabulars emmagatzemades en fitxer csv.

## 4. Limitacions de les dades

- Diferents Temps d'Actualització: Les dades d'ús de l'app i del lloc web poden ser recol·lectades i actualitzades al CRM en moments diferents.

## 5. Consideracions sobre Dades Sensibles

**Tipus de Dades Sensibles:**
- Informació Personal Identificable (PII): `Email`, `Address`
- Informació Financera Sensible: `Yearly Amount Spent`
- Dades Comportamentals Sensibles:`Avg. Session Length`, `Time on App`, `Time on Website`, `Length of Membership`

**Mesures de Protecció:**
- **Anonimització i Pseudonimització:**
  - S'aplicaran hash per a l'email i la substitució per codis per a Address.
- **Accés Restringit:**
  - Accés a dades sensibles restringit només a personal autoritzat amb necessitat de conèixer aquestes dades per a fins específics del projecte.
- **Compliment de Regulacions:**
  - Compliment amb la GDRP
