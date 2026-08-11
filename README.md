# 📋 Predicción de Demanda y Control de Inventario con Machine Learning 🤖

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Mera-15/inventory-optimization-ml/blob/main/previsión_demanda_de_articulos.ipynb)

## 📖 El origen del proyecto
Este proyecto nace de mi propia experiencia trabajando en la gestión y control de stock para una cadena de almacenes. Como encargada del seguimiento de inventario, trabajaba codo a codo con el sector de compras.

En la práctica, el control manual es un proceso altamente reactivo: los errores de carga, las mermas o la simple necesidad de "recontar para estar seguros" antes de emitir una orden de compra generaban una enorme pérdida de tiempo y recursos operativos.

**El problema:** Tomar decisiones de compra basadas únicamente en conteos manuales diarios es ineficiente y no permite anticiparse al mercado.

**La solución:** Desarrollar un modelo de Machine Learning capaz de analizar el histórico de ventas y predecir con alta precisión la demanda futura.

El objetivo de este modelo es transformar el control de inventario de un sistema reactivo a uno *proactivo*, permitiendo optimizar el tiempo del personal, agilizar las compras y asegurar el stock necesario para cada temporada.

🛠️ **Tecnologías Utilizadas:** Python(Pandas, Numpy, Plotly Express).

⚙️ **Feature Engineering:** Separé las fechas en "día", "mes", "año" y "día de la semana" para que el modelo pueda entender el paso del tiempo.

📊 **Análisis Exploratorio (EDA):** 
<img width="1743" height="472" alt="Sin título1" src="https://github.com/user-attachments/assets/6c61f134-8345-4aff-a40e-487a2a781b6d" />
En este primer gráfico se puede apreciar el volumen de mercadería que gestiona la empresa lo que sugiere que esta automatización podría ser muy beneficiosa.

<img width="1740" height="473" alt="Sin título2" src="https://github.com/user-attachments/assets/7054cbb1-6810-4195-b2fc-4819e300f9a7" />
En este segundo gráfico es fácil identificar que los picos con mayor volumen de ventas son en julio. La pregunta ahora es, ¿estas ventas son generales de la empresa o individuales de cada sucursal?

<img width="1743" height="473" alt="Sin título4" src="https://github.com/user-attachments/assets/ee6a452b-9832-4fd3-88c4-1a6ed1482443" />

**Respuesta:** Al cruzar los datos de tiempo con cada tienda específica, descubrí que todas las sucursales experimentan este mismo pico en julio. Se trata de un patrón estacional generalizado del negocio y no de un evento aislado.

Finalmente, al hacer zoom en la dinámica de una semana habitual:

<img width="1744" height="473" alt="Sin título3" src="https://github.com/user-attachments/assets/c8b9da9f-1578-42b6-9423-7037b5a344b6" />

Este gráfico muestra una tendencia clara: las ventas aumentan progresivamente a medida que se llega al fin de semana, tocando su punto máximo los domingos. Esto confirma que la variable "día de la semana" será clave para que el algoritmo anticipe la demanda.

🤖 **El Modelo Predictivo:** Para este proyecto elegí implementar un algoritmo de **Random Forest Regressor** (Bosque Aleatorio). Al tratarse de una serie de tiempo con patrones estacionales marcados, este modelo de ensamble es ideal porque puede capturar relaciones complejas no lineales entre las fechas y las ventas.

**Estrategia de Validación:**
Para evitar que el modelo haga trampa "viendo el futuro", los datos se dividieron de forma estrictamente cronológica:
* **Train (80%):** Datos históricos utilizados para que el algoritmo aprenda los patrones de demanda.
* **Test (20%):** Los meses más recientes, ocultos durante el entrenamiento, para evaluar la precisión real del modelo frente a datos desconocidos.

📈 **Resultados y Conclusiones:** Tras evaluar el modelo **Random Forest Regressor** con el 20% de los datos temporales más recientes (Test set), se obtuvieron las siguientes métricas:

* **MAE (Error Absoluto Medio):** 36.17 unidades.
* **Interpretación:** Esto significa que, en promedio, el modelo predice la demanda diaria de un artículo en una sucursal específica con un margen de error de apenas ~36 unidades.

### Conclusión del Proyecto
El Análisis Exploratorio de Datos (EDA) confirmó que las ventas de la cadena tienen una fuerte tendencia alcista a nivel anual y picos estacionales muy marcados (especialmente en el mes de julio y durante los fines de semana).

Al alimentar un algoritmo de Machine Learning con estas variables temporales procesadas, se logra crear una herramienta predictiva confiable. Para el equipo de logística y compras, implementar este modelo significa:
1. Dejar de reponer inventario basándose en la intuición.
2. Reducir el quiebre de stock durante las explosiones de ventas de mitad de año.
3. Planificar estratégicamente las entregas de proveedores para los días de menor flujo (como los lunes y martes).

### 🧠 ¿Qué aprendió el algoritmo? (Feature Importance)
Al analizar la importancia de las variables que utilizó el Random Forest Para hacer sus predicciones, se descubrió el "razonamiento" del modelo:

<img width="1743" height="467" alt="Sin título5" src="https://github.com/user-attachments/assets/7a53d35b-684a-4fb7-beca-639303b05226" />


1. **El Artículo (~53%):** Es, por lejos, la variable más decisiva. El tipo de producto define el volumen base de ventas mucho más que cualquier factor temporal.
2. **La Tienda (~16%) y el Mes (~13%):** Siguen en el ranking de importancia. Esto confirma matemáticamente lo que se descubrió visualmente en el EDA: la ubicación de la sucursal y la estacionalidad mensual (el pico de julio) son pilares fundamentales del negocio.
3. **El Día de la Semana:** Si bien no es la variable principal, le aporta al algoritmo el detalle necesario para predecir la dinámica semanal y anticiparse al salto de ventas que ocurre de viernes a domingo.
