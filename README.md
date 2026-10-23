# 🎾 Pádel Open Master — Manual & Resumen de Funciones

**Pádel Open Master** es una aplicación web integral, liviana y autónoma diseñada para organizar canchas abiertas, torneos americanos y jornadas de club. Funciona en un único archivo HTML, almacena toda la información en el navegador (`localStorage`) y no requiere servidores externos ni conexión a internet obligatoria.

---

## 1. Ciclo de Vida de Jornadas (Sesiones en Vivo)

* **Iniciar Nueva Jornada:**
  * Configuración rápida: nombre del evento, sede/club, fecha, hora y cantidad de canchas disponibles.
  * **Selección de presentes al vuelo:** Checklist de jugadores con buscador en tiempo real para marcar únicamente a quienes asistieron.
  * **Inscripción rápida (`➕ Nuevo`):** Permite registrar a un jugador nuevo directamente desde el modal de inicio sin salir ni perder selecciones.
  * **Bloqueo preventivo:** No se pueden asignar canchas ni disputar partidos sin haber iniciado formalmente una jornada.
* **Banner en Vivo:**
  * Cronómetro de duración en tiempo real (`00:00:00`).
  * Indicador de sede, fecha y contador de partidos completados.
* **Cierre y Archivado Inteligente:**
  * Al finalizar la jornada, se guarda un registro histórico con la tabla de posiciones final.
  * **Filtrado de inactivos:** Solo se guardan y archivan los jugadores que estuvieron presentes o disputaron partidos; los ausentes no ensucian la tabla histórica.
  * Reinicia automáticamente los contadores de partidos jugados del día (`PJ Hoy` y `Turnos Fuera`) manteniendo intacto el padrón y el ranking acumulado del mes.

---

## 2. Gestión de Canchas y Partidos en Tiempo Real

* **Control Dinámico de Canchas:**
  * Habilita de 1 a 12 canchas simultáneas con los botones `+` y `-`.
* **Dos Modalidades de Asignación:**
  1. **Manual (`✏️ Manual`):** Permite elegir a mano a los 4 jugadores presentes para formar la Pareja 1 y la Pareja 2.
  2. **Automático (`⚡ Auto`):** Algoritmo inteligente que empareja en segundos según el modo seleccionado.
* **Modos de Emparejamiento Automático:**
  * **Libre / Equitativo:** Prioriza turnos afuera y equilibra niveles sin importar el género.
  * **Masculino:** Exclusivo para varones en espera.
  * **Femenino:** Exclusivo para mujeres en espera.
  * **Mixto:** Garantiza 2 varones y 2 mujeres, formando duplas cruzadas (H+M vs H+M).
* **Marcador Dinámico:**
  * Inicia con 1 solo set por defecto.
  * Botón **`+ Agregar Set`** (hasta 5 sets) y opción de eliminar sets adicionales.
  * Selectores rápidos de games por equipo calibrados del **0 al 7**.
* **Sustitución en Vivo (`✏️ Cambiar Jugadores`):**
  * Permite cambiar o sustituir a cualquier jugador en una cancha activa sin perder el marcador ni los games que ya se estaban disputando.
* **Anulación Segura:**
  * Botón para anular partidos que devuelve a los 4 jugadores a la lista de espera sin computar estadísticas ni alterar puntos.

---

## 3. Algoritmo de Equidad y Balanceo de Nivel

El sistema automatizado resuelve tres problemas clave en jornadas abiertas:

1. **Prioridad de Espera (`waitTurns`):** Quienes llevan más turnos consecutivos afuera sin jugar tienen prioridad 1 para ingresar.
2. **Equidad de Partidos (`sessionMatchesPlayed`):** Desempata favoreciendo a quienes hayan jugado menos partidos hoy, logrando que todos jueguen la misma cantidad.
3. **Equiparación de Niveles (*Snake Draft*):**
   * Evalúa la destreza combinando Categoría (1ª a 9ª) y Subcategoría (Inicial, Intermedio, Avanzado).
   * Cruza las parejas: **Pareja 1 (1º + 4º mejor)** vs **Pareja 2 (2º + 3º mejor)** para asegurar partidos parejos y competitivos.

---

## 4. Padrón de Jugadores & Estadísticas de Jornada

* **Registro Completo:**
  * Nombre único (validación automática contra duplicados).
  * Género: Masculino (`H`) / Femenino (`M`).
  * Categorías: De **1ª a 9ª**.
  * Subcategorías: **Inicial**, **Intermedio** y **Avanzado**.
* **Estado de Presencia en 1 Clic:**
  * Botón directo para alternar entre `🟢 Presente` y `🔴 Ausente`.
  * Filtro rápido de vista: *Todos*, *Solo Presentes* o *Solo Ausentes*.
  * Buscador en tiempo real por texto o categoría.
* **Estadísticas de la Jornada en Vivo:**
  * `PJ Hoy` (Partidos Jugados).
  * `PG` (Ganados) y `PP` (Perdidos).
  * `% Vic` (Porcentaje de efectividad).
  * `Dif Games` (Diferencial a favor / en contra).
  * `Pts Hoy` (3 puntos por victoria, 1 punto por partido disputado).
  * `Turnos Fuera` (Contador de rotación).
* **Criterio de Ranking de la Jornada:**
  * Selector para ordenar por:
    * **Más Victorias (PG):** Desempate por `% Vic`, luego `Dif Games`.
    * **% de Victorias:** Desempate por `PG`, luego `Dif Games`.
* **Métricas de Cabecera:**
  * Conteo total de jugadores, jugadores en cancha, presentes en espera y ausentes.
  * Etiqueta de dispersión que evalúa si la rotación de partidos está equilibrada.

---

## 5. Ranking Mensual Acumulativo

* **Acumulación Continua:** Suma todos los partidos jugados y computados a lo largo del mes o del historial completo.
* **Columna "Puesto" Estática y Correlativa:**
  * Muestra las posiciones `1º, 2º, 3º, #4...` de forma consecutiva según el criterio u orden que selecciones.
  * Distintivos visuales destacados para el podio (Oro, Plata, Bronce).
* **Filtros Dinámicos e Instantáneos:**
  * **Criterio Base:** Victorias (`PG`), `% Victorias` o Partidos Jugados (`PJ`).
  * **Periodo:** Mes Actual o Histórico Total.
  * **Jornada:** Permite aislar los resultados de una jornada específica o ver todas.
  * **Categoría:** Filtrado de 1ª a 9ª.
  * **Género:** Todos, Solo Masculino o Solo Femenino.
* **Encabezados Ordenables:**
  * Al hacer clic en cualquier encabezado de columna de las tablas, se ordena de forma ascendente (`▲`) o descendente (`▼`).

---

## 6. Historial de Jornadas Archivadas

* Lista cronológica de todas las jornadas cerradas.
* Muestra sede, fecha, hora, duración, cantidad de partidos y podio de honor.
* **Botón "👁️ Ver Tabla":** Despliega la tabla final completa de posiciones de esa jornada con sus métricas.
* **Botón "🗑️":** Permite eliminar jornadas históricas individuales con confirmación de seguridad.

---

## 7. Reportes y Compartir por WhatsApp

* **Desde la barra superior:**
  * Reporte de la última jornada (Top 5 o Jornada completa).
  * Reporte mensual acumulado (Top 5 del mes o Ranking completo).
* **Desde el Historial de Jornadas:**
  * Comparte directamente el Top 5 o la tabla completa de cualquier jornada pasada.
* **Selector de Criterio para el Mensaje:**
  * Permite elegir si el reporte a enviar se clasifica por **Victorias (PG)** o por **% de Victorias**.
* **Herramientas de Envío:**
  * Vista previa del texto con formato y emojis para WhatsApp.
  * Botón para **Copiar al Portapapeles**.
  * Botón para **Abrir en WhatsApp Web / Móvil** de forma directa.

---

## 8. Seguridad, Respaldos y Exportación

* **Almacenamiento Local Automático:** Todo cambio se guarda de inmediato en el navegador del dispositivo (`localStorage`).
* **Descargar Copia Completa (.JSON):** Genera un archivo con toda la base de datos (jugadores, ranking, jornadas y partidos) para respaldar o transferir a otro organizador.
* **Restaurar Copia (.JSON):** Permite cargar la copia en otro celular o computadora en 1 segundo.
* **Exportar a Excel (.CSV):** Descarga el ranking en formato de hoja de cálculo compatible con Excel y Google Sheets.