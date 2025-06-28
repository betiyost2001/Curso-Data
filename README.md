# 🧠 Trabajo Final Integrador – Ingeniería de Datos (UTN BA)

Este proyecto corresponde al trabajo final integrador del curso de **Ingeniería de Datos** del Centro de eLearning de la UTN. Tiene como objetivo aplicar un pipeline de procesamiento de datos real, desde la extracción de una API pública hasta el almacenamiento estructurado en formato Delta Lake.

---

## 🚀 Objetivo

Simular un flujo ETL real que incluya:

- Extracción de datos desde una API externa  
- Almacenamiento incremental y full en formato Delta Lake (capa Bronze)  
- Procesamiento y transformaciones (capa Silver)  
- Agregaciones y análisis (capa Gold)

---

## 🌐 API utilizada

[Open-Meteo](https://open-meteo.com/): API meteorológica gratuita y pública.

Se consumieron dos endpoints:

- 🕒 **Dinámico (pronóstico horario)** → extracción incremental particionada  
- 🗺️ **Estático (información de ubicación)** → extracción full

---

## 🧰 Tecnologías utilizadas

- Python 3.12  
- Pandas  
- Requests  
- PyArrow  
- Delta Lake (via `deltalake`)

---

## 🗂️ Estructura del proyecto

betinayost_tp_final.py     # Script principal  
requirements.txt           # Dependencias  
README.md                  # Este archivo  
datalake_tp1/              # Capa Bronze (generada automáticamente)  
silver/                    # Capa Silver (procesamiento)  
gold/                      # Capa Gold (agregaciones)


---

## ⚙️ Instrucciones de ejecución

1. Clonar el repositorio:
   git clone https://github.com/betiyost2001/data-engineering-tp-final.git
   cd data-engineering-tp-final
   
2. Crear un entorno virtual (opcional pero recomendado):
  python -m venv venv
  venv\Scripts\activate     # En Windows


3. Instalar dependencias:
  pip install -r requirements.txt

4. Ejecutar el script:
  python betinayost_tp_final.py


📌 Detalles implementados

✅ Extracción
-requests.get() para consumir API dinámica y estática
-Guardado incremental (append) en Delta Lake, particionado por fecha y hora
-Guardado full con overwrite en datos estáticos

✅ Transformaciones
-Eliminación de duplicados
-Relleno de valores nulos
-Conversión de fechas
-Columnas derivadas (alta_temp, alta_poblacion)
-Normalización de texto

✅ Agregaciones
-groupby por fecha
-Cálculo de: temperatura promedio, máxima y mínima
-Guardado en la capa Gold

🔒 Consideraciones de seguridad
Este proyecto no utiliza datos personales sensibles ni credenciales de acceso.
Todos los datos provienen de fuentes públicas, por lo tanto no requiere anonimización ni protección especial.

👩‍💻 Autor
Betina Yost
GitHub: @betiyost2001
📧 yostbetina20@gmail.com

🏁 Estado
✅ Proyecto completado y aprobado con un 86% en la evaluación final de UTN BA.
