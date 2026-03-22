# 🧠 Justificaciones Técnicas - Ejercicio Stellar Classification

## 📋 Resumen ejecutivo de decisiones

| Problema | Decisión | Justificación breve |
|----------|----------|---------------------|
| Normalización de nombres de las columnas | Convertir los títulos de las columnas en minúsculas y reemplazar " " y "-" por "_" | Evita problemas con los nombres de las columnas en futuros análisis |
| Falta del promedio de magnitudes | Se crea la columna `magnitud_prom` | Permite identificar objetos más brillantes y más tenues |
| Lectura de fechas en formato MJD | Se crean las columnas `fecha`, `año` y `mes` | Facilita el análisis temporal (años y meses con más observaciones) |

---

## 🔍 Detalle de cada decisión técnica

### 1. Normalización de nombres de las columnas

**Cantidad:** 18 títulos de columnas (100% del total)

**Decisión:** Se convirtió los títulos de las columnas en minúsculas y se reemplazaron los espacios (" ") y los guiones medios ("-") por guion bajo ("_") para asi evitar posibles problemas en el futuro

**Código:**
```python
df.columns = (
    df.columns
    .str.lower()
    .str.replace(" ", "_")
    .str.replace("-", "_")
)

df.columns
```

---

### 2. Falta del promedio de magnitudes

**Cantidad:** 100.000 registros (100% del total)

**Decisión:** Se crea la columna `magnitud_prom` para facilitar análisis como la identificación de los objetos más brillantes y más tenues

**Código:**
```python
df['magnitud_prom'] = (df['u'] + df['g'] + df['r'] + df['i'] + df['z']) / 5
```

---

### 3. Error en la lectura de la fecha con el formato MJD

**Cantidad:** 100.000 registros (100% del total)

**Decisión:** Se crean las columnas `fecha`, `año` y `mes` a partir del MJD (Modified Julian Date) para permitir análisis temporales, como identificar los años y meses con mayor actividad de observación.

**Código:**
```python
def mjd_to_date (mjd):
    fecha_base = datetime(1858,11,17)
    dias = int(mjd)
    fraccion_dia = mjd - dias
    fecha = fecha_base + timedelta(days=dias, seconds=fraccion_dia * 24 * 3600)
    return fecha

df['fecha'] = df['mjd'].apply(mjd_to_date)
df['año'] = df['fecha'].dt.year
df['mes'] = df['fecha'].dt.month
```