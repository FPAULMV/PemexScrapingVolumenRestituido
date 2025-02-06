# Script de Automatización de Volumen Restituido Pemex

Este proyecto automatiza la recopilación, procesamiento y almacenamiento de datos del portal web de Pemex sobre volumen restituido. El script utiliza **Selenium** para interactuar con el portal web, **Pandas** para procesar los datos, y **pyodbc** para conectarse a una base de datos SQL Server.

## Descripción

1. **Conexión a la base de datos**: Se establece una conexión a una base de datos SQL Server utilizando credenciales almacenadas en un archivo de configuración.
   
2. **Extracción de la última fecha registrada**: Se realiza una consulta SQL para obtener la fecha más reciente de operación registrada en la base de datos.

3. **Automatización con Selenium**: El script utiliza Selenium WebDriver para automatizar la interacción con una página web de Pemex. Se inicia sesión en el portal utilizando las credenciales proporcionadas en el archivo de configuración.

4. **Recuperación de datos**: Para cada fecha dentro de un rango determinado, el script navega a la página de volumen restituido y extrae una tabla de datos. Los datos de la tabla son procesados y convertidos en un DataFrame de Pandas.

5. **Transformación y almacenamiento**: Los datos extraídos son limpiados, los valores numéricos son convertidos y las columnas son renombradas. Luego, los datos son insertados en una tabla de base de datos SQL Server.

6. **Eliminación de duplicados**: El script ejecuta una consulta SQL para eliminar registros duplicados basados en el campo "Remisión".

7. **Cierre de sesión y limpieza**: Después de procesar todos los datos, se cierra la sesión en el portal de Pemex y se finaliza el proceso.

## Requisitos

- Python 3.x
- Bibliotecas necesarias:
  - `pyodbc`
  - `pandas`
  - `selenium`
  - `webdriver_manager`

Instala las dependencias con el siguiente comando:

```bash
pip install pyodbc pandas selenium webdriver_manager
