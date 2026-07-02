# True Blue · Reporte Diario de Operación

Dashboard estático (GitHub Pages) para el cliente **True Blue (Proyecto SAI)**. Cada día se carga la exportación de servicios (CSV de SmartQuick, separado por `;`) y la página genera automáticamente:

- Servicios totales, finalizados y cancelados del día
- % de cumplimiento global (Finalizados / Total)
- Tabla por ciudad con servicios, finalizados, cancelados y % de cumplimiento con semáforo (verde ≥ 98%, ámbar ≥ 95%, rojo < 95%)
- Gráfica de barras apiladas por ciudad (top 10 por volumen)

Todo el procesamiento ocurre en el navegador: **el CSV nunca se sube a ningún servidor**, por lo que los datos de clientes no quedan publicados en el repositorio.

## Publicación en GitHub Pages (una sola vez)

1. Cree un repositorio nuevo en GitHub, por ejemplo `trueblue-reporte-diario` (puede ser público o privado con Pages habilitado).
2. Suba el archivo `index.html` a la raíz del repositorio.
3. Vaya a **Settings → Pages → Branch: main / (root) → Save**.
4. En 1–2 minutos la página quedará disponible en:
   `https://<su-usuario>.github.io/trueblue-reporte-diario/`

## Uso diario

1. Exporte el CSV de servicios del día desde SmartQuick.
2. Abra la URL del dashboard y arrastre el archivo (o haga clic para seleccionarlo).
3. Tome el pantallazo del reporte y compártalo con el cliente. El botón **Imprimir / PDF** genera una versión limpia si prefiere enviar PDF.
4. Para cargar otro archivo, use el botón **↺ Cargar otro archivo**.

## Requisitos del CSV

- Separador `;` (también acepta `,` — el delimitador se detecta automáticamente)
- Columnas obligatorias: `Ciudad` y `Estado`
- Columna opcional: `Fecha` (se usa para mostrar la fecha de operación en el encabezado)
- El % de cumplimiento se calcula como servicios con estado `Finalizado` sobre el total; cualquier otro estado (principalmente `Cancelado`) cuenta como cancelado y se detalla en el KPI correspondiente.
