# 📋 Predicción de Demanda y Control de Inventario con Machine Learning 🤖

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

🤖 **El Modelo Predictivo:** *(En progreso...⏳)*

📈 **Resultados y Conclusiones:** *(En progreso...⏳)*
