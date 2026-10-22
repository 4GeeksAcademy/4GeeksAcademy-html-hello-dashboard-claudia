# Fred Flintstone | Dashboard de influencer

Proyecto educativo de 4Geeks Academy para reunir los resultados de las redes sociales de Fred Flintstone, presentado como un influencer ficticio. El dashboard permitirá comparar ventas, comisiones, conversión y engagement para decidir qué productos y plataformas funcionan mejor.

## Estado del proyecto

Dashboard estático implementado con datos ficticios. No hay conexión con cuentas reales ni APIs de redes sociales. Los valores y los gráficos están definidos directamente en el HTML, sin cálculo dinámico ni filtros.

## Estructura

1. **Bloque superior: cinco KPIs.** Comisiones generadas, ventas confirmadas, conversión global, retorno publicitario y engagement global.
2. **Bloque intermedio: tres drivers.** Rendimiento por producto (barras horizontales de comisiones y listado de ventas), rendimiento por plataforma (columnas de retorno y de conversión en gráficos separados) y engagement por plataforma y producto (columnas agrupadas).
3. **Bloque inferior: detalles operacionales.** Fichas por plataforma y producto en móvil y tablet; tabla compacta en escritorio, con alcance, interacciones, ventas, comisiones, costes y retorno.

## Tecnologías y diseño

- **HTML semántico:** estructura con `header`, `nav`, `main`, `section` y `table`.
- **Tailwind CSS v4:** estilos de la interfaz exclusivamente con clases utility, sin otros frameworks de interfaz ni hojas de estilos propias.
- **Charts.css 1.2.0:** cuatro gráficos construidos con tablas HTML, sin Chart.js ni JavaScript adicional. Se utilizan variables CSS de la biblioteca para tamaños, colores y espacio de etiquetas, como excepción permitida para gráficos. Los valores permanecen en el HTML como texto.
- **Diseño mobile-first:** una columna en móvil, dos columnas de KPIs con `sm:`, tres con `md:` y cinco con `lg:`. Los drivers pasan de una a dos y luego tres columnas. Los detalles se muestran como fichas hasta tablet y como tabla compacta en escritorio, evitando el scroll horizontal de la página.
- **Consistencia:** los indicadores y gráficos compartirán patrones de estructura, espaciado y tipografía.

Dependencias incluidas en el `head`:

```html
<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/charts.css@1.2.0/dist/charts.min.css">
```

El uso de CDN requiere conexión a internet. Charts.css sustituye la propuesta inicial de Chart.js para ajustarse a las tecnologías indicadas en la tarea.

## Mock data

Todos los datos son ficticios. El período de referencia será del 1 al 30 de septiembre de 2026 y los importes se expresarán en euros.

### Productos y comisiones

Fred recibe una comisión fija del 15 % por cada venta confirmada.

| Producto | Precio (EUR) | Comisión por venta (EUR) |
| --- | ---: | ---: |
| A | 50 | 7.50 |
| B | 120 | 18.00 |
| C | 80 | 12.00 |

### Resultados por plataforma y producto

Cada fila representa el resultado mensual de un producto en una plataforma. Los puntos decimales se usan como formato numérico de referencia; la interfaz mostrará los importes con formato español.

| Plataforma | Producto | Alcance | Interacciones | Ventas | Coste publicitario (EUR) |
| --- | --- | ---: | ---: | ---: | ---: |
| Instagram | A | 10000 | 600 | 20 | 30 |
| Instagram | B | 8000 | 400 | 10 | 30 |
| Instagram | C | 12000 | 720 | 15 | 40 |
| TikTok | A | 20000 | 1600 | 30 | 40 |
| TikTok | B | 15000 | 900 | 5 | 30 |
| TikTok | C | 25000 | 2000 | 20 | 50 |
| YouTube | A | 5000 | 250 | 10 | 20 |
| YouTube | B | 7500 | 450 | 15 | 45 |
| YouTube | C | 5000 | 300 | 10 | 25 |

### Definición de las métricas

- **Ventas:** compras confirmadas; cada compra corresponde a una unidad y una conversión. No se contemplan devoluciones.
- **Volumen vendido:** ventas multiplicadas por el precio del producto. No equivale a los ingresos de Fred.
- **Comisiones:** volumen vendido multiplicado por 0,15. Estos son los ingresos de Fred.
- **Conversión (%):** ventas divididas entre alcance, multiplicado por 100.
- **Interacciones:** suma de me gusta, comentarios, compartidos y guardados.
- **Engagement (%):** interacciones divididas entre alcance, multiplicado por 100.
- **Retorno sobre gasto publicitario:** comisiones divididas entre coste publicitario, expresado como múltiplo.
- **ROI publicitario (%):** comisiones menos coste publicitario, dividido entre coste publicitario, multiplicado por 100. No incluye otros gastos del negocio.

Para simplificar el ejercicio, se asumirá que los alcances de las filas no se solapan. En datos reales no se deben sumar como usuarios únicos sin deduplicarlos. Las tasas agrupadas se calcularán a partir de las sumas, no promediando los porcentajes de las filas. Si un denominador es cero, se mostrará «No disponible».

### Totales de referencia

Estos valores servirán para comprobar que los indicadores y los gráficos utilizan los mismos datos:

| Métrica | Resultado esperado |
| --- | ---: |
| Ventas totales | 135 |
| Volumen vendido | 10.200,00 EUR |
| Comisiones totales | 1.530,00 EUR |
| Alcance agregado | 107500 |
| Interacciones totales | 7220 |
| Coste publicitario total | 310,00 EUR |
| Conversión global | 0,13 % |
| Retorno publicitario global | 4,94× |
| Engagement global | 6,72 % |

Los porcentajes se redondearán a dos decimales únicamente al mostrarlos.

## Cómo ejecutar el proyecto

Se puede abrir directamente [index.html](index.html) en el navegador. Como alternativa, instalar Flask y arrancar el servidor incluido desde la raíz del repositorio:

```bash
pip3 install flask
python3 server.py
```

Abrir `http://localhost:3000` en el navegador si se utiliza el servidor.

## Comprobaciones previstas para la entrega

- Verificar los cinco KPIs, los tres drivers y la tabla de detalles.
- Comparar los cálculos con los totales de referencia.
- Comprobar la legibilidad y la ausencia de desbordamientos de la página en móvil, tablet y escritorio.
- Revisar encabezados, etiquetas de tablas, contraste y alternativas textuales a los gráficos.
- Añadir una captura y el enlace a la demo cuando estén disponibles.

## Créditos

Proyecto basado en la plantilla [HTML Hello de 4Geeks Academy](https://github.com/4GeeksAcademy/html-hello). Fred Flintstone se utiliza únicamente como personaje ficticio para este ejercicio educativo, sin afiliación oficial.
