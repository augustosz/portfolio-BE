# Portfolio
---
## Análisis de Datos y Business Intelligence

### Análisis de Ventas E-commerce: Dashboard Interactivo en Power BI

[![Ver Dashboard](https://img.shields.io/badge/Power_BI-Ver_Dashboard-yellow?logo=PowerBI)](https://github.com/portfolio/ecommerce-sales-dashboard)

<div style="text-align: justify">Desarrollo de un dashboard completo para el análisis de ventas de una empresa e-commerce. Implementé KPIs clave como revenue, conversion rate y customer acquisition cost. Utilizé DAX para crear medidas calculadas y establecí relaciones entre múltiples tablas. El dashboard incluye filtros interactivos por período, región y categoría de producto, permitiendo drill-down para análisis detallado.</div>

<center><img src="images/ecommerce-dashboard.png"/></center>

---
### Análisis de Retención de Clientes: Cohorte Analysis con Python

[![Abrir Notebook](https://img.shields.io/badge/Jupyter-Abrir_Notebook-blue?logo=Jupyter)](projects/customer-retention-analysis.html)
[![Ver en GitHub](https://img.shields.io/badge/GitHub-Ver_en_GitHub-blue?logo=GitHub)](https://github.com/portfolio/customer-retention-cohort-analysis)

<div style="text-align: justify">Análisis completo de retención de clientes utilizando técnicas de cohorte analysis. Procesé datos de transacciones con pandas, calculé tasas de retención mensuales y visualicé los resultados con heatmaps usando matplotlib y seaborn. Identifiqué patrones de comportamiento que permitieron proponer estrategias para mejorar la retención en un 15%.</div>
<br>
<center><img src="images/cohort-analysis.png"></center>
<br>

---
### Optimización de Inventario: Análisis ABC y Forecasting

[![Abrir Notebook](https://img.shields.io/badge/Jupyter-Abrir_Notebook-blue?logo=Jupyter)](projects/inventory-optimization.html)
[![Ver en GitHub](https://img.shields.io/badge/GitHub-Ver_en_GitHub-blue?logo=GitHub)](https://github.com/portfolio/inventory-abc-forecasting)

<div style="text-align: justify">Implementé análisis ABC para clasificación de productos y desarrollé modelos de forecasting usando técnicas de series temporales. Utilicé SQL para extraer datos de ventas históricas y Python para el análisis estadístico. Los insights obtenidos permitieron optimizar niveles de stock y reducir costos de almacenamiento en un 20%.</div>
<br>
<center><img src="images/inventory-analysis.png"/></center>
<br>

---
## Análisis Exploratorio de Datos

### Análisis del Mercado Inmobiliario: EDA con Python

[![Abrir Notebook](https://img.shields.io/badge/Jupyter-Abrir_Notebook-blue?logo=Jupyter)](projects/real-estate-eda.html)
[![Ver en GitHub](https://img.shields.io/badge/GitHub-Ver_en_GitHub-blue?logo=GitHub)](https://github.com/portfolio/real-estate-market-analysis)

<div style="text-align: justify">Análisis exploratorio completo de datos inmobiliarios utilizando pandas, numpy y matplotlib. Realicé limpieza de datos, tratamiento de valores faltantes y outliers. Calculé estadísticas descriptivas, correlaciones entre variables y creé visualizaciones para identificar factores que influyen en los precios de viviendas.</div>
<br>
<center><img src="images/real-estate-eda.png"/></center>
<br>

---
### Segmentación de Clientes: RFM Analysis y Clustering

[![Abrir Notebook](https://img.shields.io/badge/Jupyter-Abrir_Notebook-blue?logo=Jupyter)](projects/customer-segmentation.html)
[![Ver en GitHub](https://img.shields.io/badge/GitHub-Ver_en_GitHub-blue?logo=GitHub)](https://github.com/portfolio/customer-rfm-clustering)

<div style="text-align: justify">Implementé análisis RFM (Recency, Frequency, Monetary) para segmentación de clientes utilizando Python. Apliqué técnicas de clustering con K-means para identificar grupos de clientes con comportamientos similares. Los resultados permitieron desarrollar estrategias de marketing personalizadas para cada segmento.</div>
<br>
<center><img src="images/customer-segmentation.png"/></center>
<br>

---
### Análisis de Tendencias de Redes Sociales: Web Scraping y Sentiment Analysis

[![Abrir Notebook](https://img.shields.io/badge/Jupyter-Abrir_Notebook-blue?logo=Jupyter)](projects/social-media-trends.html)
[![Ver en GitHub](https://img.shields.io/badge/GitHub-Ver_en_GitHub-blue?logo=GitHub)](https://github.com/portfolio/social-media-sentiment-analysis)

<div style="text-align: justify">Desarrollé un sistema automatizado para extraer y analizar sentimientos en redes sociales usando Python. Implementé web scraping con BeautifulSoup, procesamiento de texto con NLTK y análisis de sentimientos. Creé visualizaciones temporales para identificar tendencias y picos de engagement.</div>
<br>
<center><img src="images/sentiment-analysis.png"/></center>
<br>

---
## SQL y Bases de Datos

### Análisis de Rendimiento de Ventas: Consultas SQL Avanzadas

[![Ver Consultas](https://img.shields.io/badge/SQL-Ver_Consultas-orange?logo=MySQL)](https://github.com/portfolio/sales-performance-sql)

<div style="text-align: justify">Desarrollo de consultas SQL complejas para análisis de rendimiento de ventas. Implementé window functions, CTEs y subconsultas para calcular métricas de crecimiento interanual, rankings de vendedores y análisis comparativos. Optimicé queries para mejorar el performance en bases de datos de gran volumen.</div>

```sql
-- Ejemplo: Análisis de crecimiento YoY por región
WITH sales_by_month AS (
    SELECT 
        region,
        EXTRACT(YEAR FROM order_date) as year,
        EXTRACT(MONTH FROM order_date) as month,
        SUM(total_sales) as monthly_sales
    FROM sales_data 
    GROUP BY region, year, month
),
growth_analysis AS (
    SELECT 
        region,
        year,
        month,
        monthly_sales,
        LAG(monthly_sales, 12) OVER (
            PARTITION BY region 
            ORDER BY year, month
        ) as prev_year_sales,
        ROUND(
            (monthly_sales - LAG(monthly_sales, 12) OVER (
                PARTITION BY region 
                ORDER BY year, month
            )) / LAG(monthly_sales, 12) OVER (
                PARTITION BY region 
                ORDER BY year, month
            ) * 100, 2
        ) as yoy_growth_percent
    FROM sales_by_month
)
SELECT * FROM growth_analysis
WHERE prev_year_sales IS NOT NULL
ORDER BY region, year, month;
```

---
### ETL Pipeline: Automatización de Procesos de Datos

[![Ver en GitHub](https://img.shields.io/badge/GitHub-Ver_en_GitHub-blue?logo=GitHub)](https://github.com/portfolio/etl-pipeline-python-sql)

<div style="text-align: justify">Diseñé y implementé un pipeline ETL automatizado usando Python y SQL para procesar datos de múltiples fuentes. El sistema incluye validación de calidad de datos, transformaciones complejas y carga incremental. Implementé logging y manejo de errores para garantizar la confiabilidad del proceso.</div>
<br>
<center><img src="images/etl-pipeline.png"/></center>
<br>

---
## Power BI y Visualización

### Dashboard Financiero: Control de Gastos y Presupuestos

[![Ver Dashboard](https://img.shields.io/badge/Power_BI-Ver_Dashboard-yellow?logo=PowerBI)](https://github.com/portfolio/financial-control-dashboard)

<div style="text-align: justify">Desarrollo de un dashboard financiero completo con KPIs de control presupuestario, análisis de variaciones y proyecciones. Implementé medidas DAX avanzadas para cálculos de desviaciones, utilizé bookmarks para navegación y creé alertas automáticas para gastos que excedan el presupuesto.</div>
<br>
<center><img src="images/financial-dashboard.png"/></center>
<br>

---
### Análisis de Recursos Humanos: Dashboard de Talento y Performance

[![Ver Dashboard](https://img.shields.io/badge/Power_BI-Ver_Dashboard-yellow?logo=PowerBI)](https://github.com/portfolio/hr-analytics-dashboard)

<div style="text-align: justify">Dashboard integral para análisis de RRHH incluyendo métricas de rotación, satisfacción laboral, performance reviews y análisis salarial. Utilicé Power Query para limpieza de datos y creé visualizaciones interactivas que permiten análisis por departamento, antigüedad y nivel jerárquico.</div>
<br>
<center><img src="images/hr-dashboard.png"/></center>
<br>

---
## Habilidades Técnicas

### Lenguajes y Herramientas
- **Python**: pandas, numpy, matplotlib, seaborn, scikit-learn, NLTK
- **SQL**: PostgreSQL, MySQL, consultas complejas, optimización, window functions
- **Power BI**: DAX, Power Query, modelado de datos, dashboards interactivos
- **Excel**: Tablas dinámicas, funciones avanzadas, VBA básico
- **Herramientas**: Git, Jupyter Notebooks, VS Code

### Competencias Clave
- **Análisis Exploratorio de Datos (EDA)**: Limpieza, transformación y análisis estadístico
- **Visualización de Datos**: Creación de dashboards y reportes ejecutivos
- **Business Intelligence**: Desarrollo de KPIs y métricas de negocio
- **Bases de Datos**: Diseño, consultas y optimización
- **Automatización**: Scripts para procesos ETL y reporting automático

---
## Certificaciones y Formación

- **Tecnicatura en analisis de sistemas informaticos** - *Completado 2024*
- **SQL avanzado** - *Udemy, 2024*
- **Python para ciencia de datos** - *Silicon Misiones, 2024*

---
## Contacto

📧 **Email**: [dossantosaugusto36@gmail.com](mailto:mi.email@ejemplo.com)  
💼 **LinkedIn**: [https://www.linkedin.com/in/augusto-dos-santos-a226622b6/](https://www.linkedin.com/in/augusto-dos-santos-a226622b6/)  
🐙 **GitHub**: [github.com/augustosz](https://github.com/augustosz)  
📍 **Ubicación**: Paraná, Entre Ríos, Argentina

---
<center>© 2025 [Augusto Dos Santos]. Portfolio de Analista de Datos Junior.</center>