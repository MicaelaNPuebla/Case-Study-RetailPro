# Case-Study
# RetailPro — Análisis de Ventas y Operaciones en E-commerce

Análisis de datos de punta a punta sobre 34.500 transacciones de un e-commerce, desde el modelado en SQL hasta un dashboard de negocio en Power BI. El objetivo no fue describir qué pasó, sino encontrar **dónde se pierde dinero y qué hacer al respecto**.

**Stack:** SQL (PostgreSQL) · Python (pandas, matplotlib) · Power Query (ETL) · DAX · Power BI

---

## 🎯 La pregunta de negocio

> En un e-commerce con ventas estables, ¿dónde se está perdiendo rentabilidad y por qué?

## 🔑 Hallazgo principal

**1 de cada 6 órdenes (17,7%) generaba margen negativo — y el driver no era el descuento, sino el tamaño del ticket.**

- El **49,2%** de las órdenes menores a USD 25 perdían dinero.
- Las órdenes mayores a USD 100 no perdían **ninguna**.
- El costo fijo de procesar y enviar una orden chica se come el margen.

**Recomendación:** establecer un umbral de compra mínima (o envío pago por debajo de cierto monto). Es una palanca directa sobre la rentabilidad, sin tocar la política de descuentos.

## 📊 Otros insights

- **Concentración de ingresos:** Electronics representa ~45% de la facturación → categoría crítica para disponibilidad de stock.
- **Devoluciones:** Fashion (7,7%) y Electronics (6,8%) por encima de la media (5,5%) → foco en descripciones y guía de talles.
- **Estacionalidad:** ventas planas mes a mes → la palanca de crecimiento no es la temporada, sino el ticket y la recurrencia.

---

## 🛠️ Metodología

| Etapa | Herramienta | Qué se hizo |
|---|---|---|
| Exploración (EDA) | Python (pandas, matplotlib) | Entender la forma de los datos y detectar los hallazgos que guiaron el dashboard |
| Modelado | SQL / PostgreSQL | Esquema estrella: `D_clientes`, `D_productos`, `D_fecha`, `F_ventas` (hechos) |
| Transformación (ETL) | Power Query (M) | Tipado, columnas derivadas (AñoMes, RangoTicket, MargenNegativo), tabla calendario |
| Métricas | DAX | KPIs y medidas de rentabilidad |
| Visualización | Power BI | Dashboard para marketing con storytelling (títulos narrativos) |

### Decisión de datos a destacar
Los `customer_id` y `product_id` del dataset **no eran claves estables** (un mismo ID aparecía con atributos contradictorios entre filas). Se aplicó una regla **SCD tipo 1** ("la transacción más reciente gana") para canonicalizar las dimensiones y garantizar integridad referencial.

---

## 📁 Contenido del repositorio
 
- **`RetailPro - Case Study.pdf`** — el caso completo: contexto, dataset, EDA, modelo + SQL, Power Query, dashboard en Power BI y conclusiones, con capturas de todo el proceso.
- **`README.md`** — este resumen ejecutivo.
 
## 📦 Dataset
 
*E-commerce Sales Transactions* (Kaggle, autor: miadul). 34.500 transacciones, período 2023-09-11 a 2025-09-10. Dataset público de origen sintético, usado con fines de práctica.
 
---
 
## 👤 Autora
 
**Micaela Puebla** — Analista de Datos
[LinkedIn](https://linkedin.com/in/micaela-puebla) · pueblamicaela00@gmail.com · Mendoza, Argentina
 
*Proyecto Integrador Final del curso Data Analytics (Coderhouse, 2026).*
 
