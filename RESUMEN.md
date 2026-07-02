# Fase Final Mundial ADES

## Archivos

- `index.html`: simulador independiente para 16avos en adelante.
- `ejemplo-apuesta-ficticia.html`: ejemplo ficticio del archivo que descarga una persona, con tabla visible de clasificados, forma y marcador.
- El tablero anterior de fase de grupos queda en `../16avos/index.html` como referencia y consulta.

## Flujo de uso

1. El apostador abre `index.html`.
2. Revisa las reglas visibles en el inicio.
3. Entra por **Apuesta 8vos** cuando haya cruces de octavos definidos.
4. Llena su nombre.
5. En cada cruce toca el equipo que clasifica, elige cómo clasifica y escribe un solo marcador.
6. Descarga sus resultados y los envía por WhatsApp. Por dentro sigue siendo un archivo HTML para que el admin lo pueda importar.
7. Cualquier persona puede entrar por **Seguir resultados** para ver la llave del torneo, la tabla de posiciones y los resultados que el admin va cargando.
8. El admin desbloquea con clave, importa los HTML recibidos, carga resultados reales y exporta el HTML actualizado.
9. Cuando termine una ronda, el admin cambia la ronda abierta para que la gente apueste la siguiente.

## Sistema de puntos propuesto

Máximo por partido: 10 puntos.

- 3 puntos: acierta el equipo clasificado.
- 5 puntos: acierta el marcador exacto. Si la forma fue tiempo reglamentario, el marcador corresponde a los 90 minutos. Si la forma fue prórroga o penales, corresponde al marcador tras 120 minutos, sin contar tiros penales.
- 2 puntos: acierta la forma de clasificación, entre tiempo reglamentario, prórroga o penales. Estos 2 puntos solo cuentan si también acertó el clasificado.

Motivo: el clasificado es lo más importante, el marcador exacto sigue siendo el logro más difícil, y la forma de clasificación suma un bonus sin pesar tanto como el ganador o el marcador.

## Desempates

1. Más puntos totales.
2. Más clasificados acertados.
3. Más marcadores exactos.
4. Más formas de clasificación acertadas.
5. Nombre en orden alfabético.

## Cruces y horarios

Los cruces de 16avos se cargaron con hora Colombia. Tomé como base la lista de partidos publicada para la ronda de 32 y convertí los horarios Eastern a Colombia restando una hora.

Fuentes usadas:

- SBNation: `https://www.sbnation.com/soccer/1120771/world-cup-schedule-scores-round-32`
- FIFA scores/fixtures: `https://www.fifa.com/en/tournaments/mens/worldcup/canadamexicousa2026/scores-fixtures`
- Knockout stage/formato: `https://en.wikipedia.org/wiki/2026_FIFA_World_Cup_knockout_stage`

## Notas técnicas

- El HTML es autocontenido, sin dependencias externas.
- Las apuestas descargadas muestran una tabla visible con todos los partidos, clasificado, forma y marcador; además incluyen un `embedded-state` con los picks del apostador para que el admin las pueda importar.
- El formulario de apuesta tiene autoguardado local del nombre y los picks de la ronda en curso, para que no se pierda si recargan o cierran el navegador.
- Si el navegador tiene datos locales del tablero, aparece un aviso con **Usar versión publicada** para borrar esos cambios locales y recargar el HTML publicado. No borra el borrador de apuesta.
- El admin puede importar múltiples HTML a la vez.
- El botón de envío intenta compartir el archivo desde iPhone/Android usando el menú nativo. Si el navegador no permite adjuntar archivos, descarga el HTML y abre WhatsApp al número `573132776899` con el mensaje listo.
- Los resultados reales se guardan en el navegador y también quedan embebidos al exportar el HTML actualizado.
- La tabla de posiciones aparece aunque todavía no haya apuestas importadas, con una fila de estado vacío.
- La vista de llave usa columnas por ronda y muestra de qué partidos vienen los ganadores; se alimenta de los resultados cargados por el admin y muestra campeón cuando se defina la final.
- La pantalla principal incluye buscador, accesos rápidos desplazables arriba, panel admin visible, tabla, detalle por participante y últimos puntos por partido cargado.
- La apuesta de 16avos quedó cerrada visualmente; la acción principal de apuesta ahora apunta a 8vos y solo permite descargar los cruces de octavos que ya estén definidos.
- Estado actual: 13 participantes reales de 16avos importados en `index.html`; `Andres G` quedó restaurado como participante aparte de `Alberto Gamba`.
- Laura G fue cargada desde `Fase Final Mundial ADES.pdf`; el cruce #73 quedó como Sudáfrica 0 - Canadá 0, Canadá por penales, y el #76 como Brasil 2 - Japón 1.
- Resultados reales cargados: Canadá venció 1-0 a Sudáfrica en tiempo reglamentario; Brasil venció 2-1 a Japón en tiempo reglamentario; Paraguay empató 1-1 con Alemania y clasificó por penales; Marruecos empató 1-1 con Países Bajos y clasificó por penales; Noruega venció 2-1 a Costa de Marfil en tiempo reglamentario; Francia venció 3-0 a Suecia en tiempo reglamentario; México venció 2-0 a Ecuador en tiempo reglamentario; Inglaterra venció 2-1 a RD Congo en tiempo reglamentario; Estados Unidos venció 2-0 a Bosnia en tiempo reglamentario; Bélgica venció 3-2 a Senegal en prórroga.
- El panel admin ahora recalcula tabla, llave, últimos puntos y detalle apenas se cambian campos de resultados; además un resultado oficial completo ya no queda tapado por intentos locales incompletos guardados en el navegador.
- Si una apuesta de tiempo reglamentario o prórroga tiene marcador no empatado, el sistema deduce el clasificado desde el marcador para evitar errores cuando el selector manual contradice los goles.
- El botón **Ver resultados** abre un panel flotante con la apuesta completa del participante, para no tener que bajar hasta el detalle inferior.
- La tabla permite abrir el detalle de cada participante y ver su marca de envío, archivo origen y picks completos.
