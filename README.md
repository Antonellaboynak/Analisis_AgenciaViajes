# 🧳 Análisis de Ventas — Agencia de Viajes

Análisis completo de datos de ventas de una agencia de viajes argentina con datos anonimizados de un año, con foco en rentabilidad, performance de vendedores y comportamiento por destino y sucursal.

---

## 📌 Descripción del proyecto

Este proyecto toma un listado real de reservas de una agencia de viajes y realiza un análisis end-to-end que abarca desde la carga y limpieza de los datos hasta la visualización de los principales indicadores de negocio.

Los datos corresponden a reservas con destinos al exterior y contienen información de ventas, costos, cobros, vendedores, destinos y sucursales en USD.

---

## 🛠️ Stack tecnológico

| Herramienta | Uso |
|---|---|
| **MySQL** | Almacenamiento, limpieza y análisis de datos |
| **Python** | Conexión a la base de datos y visualizaciones |
| **pandas** | Manipulación de datos |
| **Matplotlib** | Gráficos estáticos y tarjetas de KPIs |
| **Seaborn** | Gráficos estadísticos |
| **Plotly Express** | Gráficos interactivos |
| **Jupyter Notebook** | Entorno de análisis y presentación |
| **SQLAlchemy** | Conexión Python → MySQL |
| **python-dotenv** | Gestión segura de credenciales |

---

## 📁 Estructura del proyecto

```
agencia-viajes-analisis/
│
├── analisis_agencia.sql       ← Queries SQL: creación de tablas, KPIs y análisis
├── Agencia.ipynb              ← Notebook con conexión, queries y visualizaciones
├── .env                       ← Credenciales (no incluido en el repositorio)
├── .gitignore                 ← Excluye el .env del repositorio
└── README.md
```

---

## 🗄️ Análisis en SQL

El archivo `analisis_agencia.sql` contiene las siguientes consultas:

- **Creación de esquema y tablas** — tabla original `listado_agencia` y tabla resumida `listado_agencia_resumido` con las columnas necesarias para el análisis
- **KPIs anuales** — venta total, costo total, margen, ticket promedio y reservas no cobradas
- **Análisis mensual** — evolución de reservas, ventas y margen usando window functions (`AVG OVER`)
- **Ventas por región** — clasificación de destinos mediante `CASE WHEN` + `REGEXP`
- **Margen por departamento** — rentabilidad por sucursal
- **CTE + Ranking de vendedores** — clasificación por categoría de performance usando `WITH` y `RANK()`
- **Window functions** — acumulado mensual y variación vs mes anterior con `SUM OVER` y `LAG`
- **Subconsulta** — top 3 vendedores por departamento con `RANK() PARTITION BY`

---

## 📊 Visualizaciones

El notebook `Agencia.ipynb` incluye los siguientes gráficos, todos en paleta de violetas:

| # | Gráfico | Librería |
|---|---|---|
| 1 | Tarjetas de KPIs generales | Matplotlib |
| 2 | Evolución mensual de ventas USD | Matplotlib |
| 3 | Margen mensual USD | Matplotlib |
| 4 | Cantidad de reservas por destino | Matplotlib |
| 5 | Ranking de vendedores por reservas | Seaborn |
| 6 | Margen por departamento / sucursal | Matplotlib |
| 7 | Participación de ventas por región (donut) | Plotly Express |
| 8 | Participación de reservas por sucursal (donut) | Plotly Express |

---

## ⚙️ Cómo ejecutar el proyecto

### 1. Clonar el repositorio
```bash
git clone https://github.com/tu-usuario/agencia-viajes-analisis.git
cd agencia-viajes-analisis
```

### 2. Instalar dependencias
```bash
pip install pandas sqlalchemy pymysql matplotlib seaborn plotly python-dotenv jupyter
```

### 3. Configurar credenciales
Crear un archivo `.env` en la raíz del proyecto:
```
DB_HOST=localhost
DB_USER=tu_usuario
DB_PASS=tu_contraseña
DB_NAME=agencia_viajes
DB_PORT=3306
```

### 4. Cargar los datos en MySQL
Ejecutar el archivo `analisis_agencia.sql` en MySQL Workbench y luego importar el CSV con los datos.

### 5. Ejecutar el notebook
```bash
jupyter notebook Agencia.ipynb
```

---
## 👤 Autor

**Antonella Boynak**  
